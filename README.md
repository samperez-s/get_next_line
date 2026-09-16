# 42 School - get_next_line

![Language](https://img.shields.io/badge/Language-C-blue.svg)
![42 School](https://img.shields.io/badge/School-42-000000.svg)

## 📌 Overview

**get_next_line** is a fundamental project in the 42 School Common Core curriculum. The goal of this project is to code a C function that reads and returns a single line from a file descriptor (`fd`) each time it is called, terminated by a newline character (`\n`) or EOF (End of File).

This project deepens understanding of low-level I/O operations, static variables in C, dynamic memory allocation, and efficient buffer management.

---

## 🛠 Key Features & Concepts

* **Static Variables:** Utilizes static state variables to retain remaining unread buffer data across multiple function calls.
* **Buffer Management:** Operates reliably regardless of the `BUFFER_SIZE` macro value specified at compilation (from `1` to `10000000`).
* **Multi-FD Support (Bonus):** Manages multiple file descriptors simultaneously without losing the reading thread of any file.
* **Memory Safety:** Prevents memory leaks by ensuring all allocated heap memory for buffers and dynamic strings is safely freed.

---

## ⚙️ Function Prototype

```c
char *get_next_line(int fd);
Parameters: fd — The file descriptor from which to read.
```

Return Value:

```C
char * // A string containing the read line (including \n if present).

NULL // If there is nothing left to read or an error occurs.
```

🚀 Compilation & Usage
Prerequisites
A standard C compiler (gcc or clang).

Compiling with your Code
To compile get_next_line alongside your main program, include the source files and set your desired BUFFER_SIZE:

```bash
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=42 main.c get_next_line.c get_next_line_utils.c -o gnl_test
```

Code Example
```C
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include "get_next_line.h"

int main(void)
{
    int   fd;
    char  *line;

    fd = open("example.txt", O_RDONLY);
    if (fd < 0)
        return (1);
    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return (0);
}
```
