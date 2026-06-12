---
title: "Usage of Meschach library"
date: 2010-08-11
forum: General Help
---

### Post by cirobr on 2010-08-11
Hello,

I use Codeblocks as IDE environment for my C programs. I recently added the matrix library Meschach, but unfortunately the headers are not found during compiling/linking process.

For instance, my generic program is the one below:

```
#include <stdio.h>
#include <stdlib.h>
#include <matrix.h>

int main()
{
    printf("Hello world!\n");
    return 0;
}

```

This program generates the following error during compilation:

> main.c|3|error: matrix.h: No such file or directory|

And the declaration <matrix.h> is supposed to include the Meschach library, according to the instruction on the below link:

[http://www.math.uiowa.edu/~dstewart/meschach/html_manual/manual.html]("http://www.math.uiowa.edu/~dstewart/meschach/html_manual/manual.html")

Furthermore, I see on folder /usr/include the following:
[LIST]
[*]File stdio.h;
[*]Filestdlib.h;
[*]Folder "Meschach", which contains the file "matrix.h".
[/LIST]

Any help is greatly appreciated.

Thanks.

---

### Post by cirobr on 2010-08-11
Just found the answer here

[http://wiki.codeblocks.org/index.php?title=FAQ#Q:_I_would_like_to_compile_a_project_using_some_non-standard_libraries._How_can_I_indicate_to_CodeBlocks_that_these_libraries_and_include_files_exist.3F]("http://wiki.codeblocks.org/index.php?title=FAQ#Q:_I_would_like_to_compile_a_project_using_some_non-standard_libraries._How_can_I_indicate_to_CodeBlocks_that_these_libraries_and_include_files_exist.3F")

---

