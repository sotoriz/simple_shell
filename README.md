# 0x16. C - Simple Shell

##  Resources

[unix shell](https://en.wikipedia.org/wiki/Unix_shell)

## Brief discription

- To write a simple UNIX command interpreter.

## Requirements

### General

- Write a README with the description of your project
- You should have an AUTHORS file at the root of your repository, listing all individuals having contributed content to the repository.

## More Info

### Output

- Unless specified otherwise, your program must have the exact same output as sh (/bin/sh) as well as the exact same error output.
- The only difference is when you print an error, the name of the program must be equivalent to your argv[0] (See below)

#### Example of error with sh:

           $ echo "qwerty" | /bin/sh
           /bin/sh: 1: qwerty: not found
           $ echo "qwerty" | /bin/../bin/sh
           /bin/../bin/sh: 1: qwerty: not found
           $

## List of allowed functions and system calls

- `access`
- `chdir`
- `close`
- `closedir`
- `execve`
- `exit`
- `_exit`
- `fflush`
- `fork`
- `free`
- `getcwd`
- `getline`
- `getpid`
- `isatty`
- `kill`
- `malloc`
- `open`
- `opendir`
- `perror`
- `read`
- `readdir`
- `signal`
- `stat`
- `lstat`
- `fstat`
- `strtok`
- `wait`
- `waitpid`
- `wait3`
- `wait4`
- `write`

## Compilation

gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c -o hsh

## Testing

Your shell should work like this in interactive mode:

         $ ./hsh
         ($) /bin/ls
         hsh main.c shell.c
         ($)
         ($) exit
         $
But also in non-interactive mode:

         $ echo "/bin/ls" | ./hsh
         hsh main.c shell.c test_ls_2
         $
         $ cat test_ls_2
         /bin/ls
         /bin/ls
         $
         $ cat test_ls_2 | ./hsh
         hsh main.c shell.c test_ls_2
         hsh main.c shell.c test_ls_2
         $

## Tasks

### mandatory

### 0. Betty would be proud

Write a beautiful code that passes the Betty checks

### 1. Simple shell 0.1

Write a UNIX command line interpreter.

- Usage: `simple_shell`

Your Shell should:


- Display a prompt and wait for the user to type a command. A command line always ends with a new line.
- The prompt is displayed again each time a command has been executed.
- The command lines are simple, no semicolons, no pipes, no redirections or any other advanced features.
- The command lines are made only of one word. No arguments will be passed to programs.
- If an executable cannot be found, print an error message and display the prompt again.
Handle errors.
- You have to handle the “end of file” condition Ctrl+D

You don’t have to:

- use the PATH
- implement built-ins
- handle special characters : ", ', `, \, *, &, #
- be able to move the cursor
- handle commands with arguments

### 2. Simple shell 0.2

Simple shell 0.1 +

- Handle command lines with arguments

### 3. Simple shell 0.3

Simple shell 0.2 +

- Handle the PATH
- `fork` must not be called if the command doesn’t exist

### 4. Simple shell 0.4

Simple shell 0.3 +

- Implement the `exit` built-in, that exits the shell
- Usage: `exit`
- You don’t have to handle any argument to the built-in `exit`

### 5. Simple shell 1.0

Simple shell 0.4 +

- Implement the `env` built-in, that prints the current environment

### Advance

### 6. Simple shell 0.1.1

Simple shell 0.1 +

- Write your own `getline` function
- Use a buffer to read many chars at once and call the least possible the `read` system call
- You will need to use `static` variables
- You are not allowed to use `getline`

You don’t have to:

- be able to move the cursor

### 7. Simple shell 0.2.1

Simple shell 0.2 +

- You are not allowed to use `strtok`

### 8. Simple shell 0.4.1

Simple shell 0.4 +

- handle arguments for the built-in `exit`
- Usage: `exit status`, where status is an integer used to exit the shell

### 9. setenv, unsetenv

Simple shell 1.0 +

Implement the setenv and unsetenv builtin commands

- `setenv`

  - Initialize a new environment variable, or modify an existing one
  - Command syntax: `setenv VARIABLE VALUE`
  - Should print something on stderr on failure

- `unsetenv`

  - Remove an environment variable
  - Command syntax: `unsetenv VARIABLE`
  - Should print something on stderr on failure

### 10. cd

Simple shell 1.0 +

Implement the builtin command `cd`:

- Changes the current directory of the process.
- Command syntax: `cd [DIRECTORY]`
- If no argument is given to `cd` the command must be interpreted like cd `$HOME`
- You have to handle the command `cd -`
- You have to update the environment variable `PWD` when you change directory

`man chdir, man getcwd`

### 11. ;

Simple shell 1.0 +

- Handle the commands separator `;`

### 12. && and ||

Simple shell 1.0 +

- Handle the `&&` and `||` shell logical operators

### 13. alias

Simple shell 1.0 +

- Implement the `alias` builtin command
- Usage: `alias [name[='value'] ...]`

  - `alias`: Prints a list of all aliases, one per line, in the form `name='value'`
  - `alias name [name2 ...]`: Prints the aliases `name, name2`, etc 1 per line, in the form `name='value'`
  - `alias name='value' [...]`: Defines an alias for each `name` whose `value` is given. If `name` is already an alias, replaces its value with `value`

### 14. Variables

Simple shell 1.0 +

- Handle variables replacement
- Handle the `$?` variable
- Handle the `$$` variable

### 15. Comments

Simple shell 1.0 +

- Handle comments (`#`)

### 16. File as input

Simple shell 1.0 +

- Usage: `simple_shell [filename]`
- Your shell can take a file as a command line argument
- The file contains all the commands that your shell should run before exiting
- The file should contain one command per line
- In this mode, the shell should not print a prompt and should not read from `stdin`
