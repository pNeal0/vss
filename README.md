# Very Simple Shell

A basic shell implementation in Python, with the goal of being as simple as possible.\
No scripting, piping, expansion, etc.

## Built-in Commands

* cd		- Change directory
* ls		- List all the files in a directory
* pwd		- Print the current working directory
* mkdir		- Create an empty directory
* setenv	- Set environment variable
* getenv	- Print environment variable
* mode		- Print permissions of a file
* sig		- Send a signal to a process
* help		- Print command usage

## Usage

To run the shell, simply execute the 'vss' script.\
To exit the shell, send an EOF signal (ctrl + D).

### Whitespaces
If you want to use a whitespace, Ex:
```
cp "bad filename 1" "bad filename 2"
```
You need to substitute it with a backslash:
```
cp bad\filename\1 bad\filename\2
```

## Customization

### Prompt

To customize the prompt, You need to modify ```get_prompt()``` return value.\
For example, You could have a green CWD displayed:

```python
def get_prompt():
    prompt = termcolor.colored(os.getcwd(), "green")
    return prompt+"$ "
```

Default does not include any coloring.

### Features

The script is really short and easy to read, so modifying it is very straightforward.

For example, to add a built in command:
1. Define a function:
```python
def print_heart():
	print("<3")
```

2. Map a command(alias) to the function name:
```python
BUILTINS {
"heart": print_heart,
# ...
}
```

3. That's it!
```
~ $ heart
<3
~ $
```
