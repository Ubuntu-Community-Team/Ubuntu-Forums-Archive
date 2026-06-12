---
title: "Shell Script for Opencv Compilation"
date: 2010-05-30
forum: General Help
---

### Post by tuxmanic on 2010-05-30
Hello Friends.


I installed **Opencv** in **Lucid**.But i dont know how to compile a program (.c/.cpp) by giving additional opencv flags. So i found another method, There is Buildall.sh (given Below) along with the samples in Opencv Source.I copied buildall.sh to my working directory and using it but there is a problem that each time it compile all the source files in the .


But what i need is a "build.sh" file such that it compile only the argument file given from terminal using opencv flags as in buildall.sh. like follows

       ```
 sh ./build.sh prog.c      
```    then it will compile prog.c

      ```
 sh ./build.sh prog2.cpp
```    then it will compile prog2.cpp 

Please help me..  its for my project .imy entire project using opensource tools and softs only. Thanks in advance.if possible somone pls explain the shell script in build all.sh

**buildall.sh**
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```
#!/bin/sh

if [[ $# > 0 ]] ; then
    base=`basename $1 .c`
    echo "compiling $base"
    gcc -ggdb `pkg-config opencv --cflags --libs` $base.c -o $base 
else
    for i in *.c; do
        echo "compiling $i"
        gcc -ggdb `pkg-config --cflags opencv` -o `basename $i .c` $i `pkg-config --libs opencv`;
    done
    for i in *.cpp; do
        echo "compiling $i"
        g++ -ggdb `pkg-config --cflags opencv` -o `basename $i .cpp` $i `pkg-config --libs opencv`;
    done
fi
```

---

### Post by geirha on 2010-05-30
That script contains [bashism](https://wiki.ubuntu.com/DashAsBinSh/), which means it will not work on Ubuntu. A quick fix is to change 
```
[[ $# > 0 ]]
```
to
```
[ $# -gt 0 ]
```
Though, a better approach would be to use make.

---

### Post by tuxmanic on 2010-05-30
> **geirha said:**
> That script contains [bashism]("https://wiki.ubuntu.com/DashAsBinSh/"), which means it will not work on Ubuntu. A quick fix is to change 
```
[[ $# > 0 ]]
```to
```
[ $# -gt 0 ]
```Though, a better approach would be to use make.

Thanks for the reply. I dont know much about Shell scripting .anyway  buildall.sh is working fine, am telling you this because am using it in both Jaunty & lucid.  am attaching a processed image ( Face detection).

---

### Post by geirha on 2010-05-30
Well, if you run it without arguments
```
./buildall.sh
``` it will just try to execute the [[ command, which does not exist, so it fails and skips to the else part.

Now, if you fix the script as I explained, you can run ```
./buildall.sh prog.c
``` to have it compile only that c-file. It will not, however, work for .cpp files.

This script should (though I haven't tested it):
```

#!/bin/sh

for file; do
  base=${file%.*}
  case $file in 
    *.c)
      echo "Compiling $base"
      gcc -ggdb $(pkg-config --cflags --libs opencv) -o "$base" "$file"
      ;;
    *.cpp)
      echo "Compiling $base"
      g++ -ggdb $(pkg-config --cflags --libs opencv) -o "$base" "$file"
      ;;
    *)
      echo "Don't know what to do with $file"
      ;;
  esac
done

```

---

### Post by tuxmanic on 2010-05-30
[LEFT][B]Thank uou [geirha ]("http://ubuntuforums.org/member.php?u=243323")Its working... :KS

[/B]Could you please explain the Orginal buildall.sh and yours . i have some doubts 

There are three cases in the orginal buildall.sh . two for .c files and one for .cpp , why there is two cases for .c files ?.

 

[/LEFT]

---

### Post by geirha on 2010-05-30
Well, in pseudo C-code, the original script basicly does

```

if (argc > 1) {
  build_c_file(argv[1]);
} else {
  build_all_c_files_in_cwd();
  build_all_cpp_files_in_cwd();
}

```

Well, actually [[ $# > 0 ]] does not compare integers, but rather does a sprintf(tmp,"%d",argc-1); if ( strcmp(tmp,"0") > 0 ) which just happens to give the same result. (( $# > 0 )) or [ $# -gt 0 ] would do integer comparison.

The script I made, roughly does
```

build_c_and_cpp_files(argv);

```

Hope that made sense :)

---

