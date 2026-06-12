---
title: "compile problem"
date: 2010-04-09
forum: General Help
---

### Post by kanew1994 on 2010-04-09
hi guys,
I'm new to ubuntu and need some help with my compiler.
I installed the compiler and opencv lib.
When I compiled my code, still got some problems.

kane@kane-laptop:~/Desktop$ gcc -o hello hello.cpp
hello.cpp:1:14: error: #include expects "FILENAME" or <FILENAME>
hello.cpp:2:14: error: #include expects "FILENAME" or <FILENAME>
hello.cpp:3:14: error: #include expects "FILENAME" or <FILENAME>
hello.cpp: In function ‘int main(int, char**)’:
hello.cpp:6: error: ‘IplImage’ was not declared in this scope
hello.cpp:6: error: ‘img’ was not declared in this scope
hello.cpp:7: error: ‘printf’ was not declared in this scope
hello.cpp:9: error: ‘cvLoadImage’ was not declared in this scope
hello.cpp:13: error: ‘CV_WINDOW_AUTOSIZE’ was not declared in this scope
hello.cpp:13: error: ‘cvNamedWindow’ was not declared in this scope
hello.cpp:14: error: ‘cvShowImage’ was not declared in this scope
hello.cpp:15: error: ‘cvWaitKey’ was not declared in this scope
hello.cpp:16: error: ‘cvDestroyWindow’ was not declared in this scope

Can anyone help me figure it out?
thanks.

---

### Post by moetunes on 2010-04-09
You might need to ask this in   programming help   but it seems you missed the #includes at the start of your prog :)

---

### Post by falconindy on 2010-04-09
The includes seem to be there, but improperly declared. Header files taken from your include path should declared as:
```
#include <stdio.h>
```

Includes in the same directory as the source should be:
```
#include "foo.h"
```

---

### Post by moetunes on 2010-04-09
>  hello.cpp:1:14: error: #include expects "FILENAME" or <FILENAME>
says you're not setting things up right at the start
like
[falconindy]("http://ubuntuforums.org/member.php?u=863375")
says

---

### Post by tuxmanic on 2010-07-18
> kane@kane-laptop:~/Desktop$ gcc -o hello hello.cpp
hello.cpp:1:14: error: #include expects "FILENAME" or <FILENAME>
hello.cpp:2:14: error: #include expects "FILENAME" or <FILENAME>
hello.cpp:3:14: error: #include expects "FILENAME" or <FILENAME>
hello.cpp: In function &#8216;int main(int, char**)&#8217;:
hello.cpp:6: error: &#8216;IplImage&#8217; was not declared in this scope
hello.cpp:6: error: &#8216;img&#8217; was not declared in this scope
hello.cpp:7: error: &#8216;printf&#8217; was not declared in this scope
hello.cpp:9: error: &#8216;cvLoadImage&#8217; was not declared in this scope
hello.cpp:13: error: &#8216;CV_WINDOW_AUTOSIZE&#8217; was not declared in this scope
hello.cpp:13: error: &#8216;cvNamedWindow&#8217; was not declared in this scope
hello.cpp:14: error: &#8216;cvShowImage&#8217; was not declared in this scope
hello.cpp:15: error: &#8216;cvWaitKey&#8217; was not declared in this scope
hello.cpp:16: error: &#8216;cvDestroyWindow&#8217; was not declared in this scope
Seems that you are trying to compile a programme having opencv functions.To compile such a programme you also need to include the associated header files first.

For example the openCv function ***cvNamedWindow*** requires the header file ***highgui.h ***

So make sure that you included all the **associated header files first.**

Here is a sample OpenCv programme.

```
/* 
About                : simple OpenCV program that loads an image from disk and displays it on the screen
Orginal Source :Learning OpenCV: Computer Vision with the OpenCV Library(ISBN:0596516134, Publisher: O'Reilly Media),  Example 2-1. A, 
Modified By       : Jomon John <tuxmanic[at]gmail[dot]com>
Date                  : 31-05-2010*/
Tested on         : OpenCV-2.1.0

#include <cv.h>
#include <highgui.h>
#include <stdio.h>

int main( int argc,char** argv){
    if( argv[1] == NULL ){
        printf("\n Please Provide a valid Argument \n");
        return(0);
    }
    else{
        IplImage* img = cvLoadImage(argv[1],CV_LOAD_IMAGE_UNCHANGED);
        cvNamedWindow("Image",CV_WINDOW_AUTOSIZE);
        cvShowImage("Image",img);
        printf("\n Press 'Esc' Key to Exit \n");
        while(1){
        char c = cvWaitKey(0);
        if(c == 27) break;
        }
        cvReleaseImage(&img);
        cvDestroyWindow("Image");
        return(0);
    }

}

```> kane@kane-laptop:~/Desktop$ gcc -o hello hello.cppAlso for successful build you have to compile with opencv flags.that means you cant just compile as you tried.

i have alredy made a short post describing easy comilation with opencv, [COLOR=Blue][check here]("http://ubuntuforums.org/showpost.php?p=9603750&postcount=2")[/COLOR]


Looks like you are not familar with opencv . Dont worry its really easy.Please reading the following resources first


[LIST=1]
[*]The OpenCV book: [COLOR=Blue][Learning OpenCV]("http://www.amazon.com/Learning-OpenCV-Computer-Vision-Library/dp/0596516134")[/COLOR][URL="http://www.amazon.com/Learning-OpenCV-Computer-Vision-Library/dp/0596516134"] 
[/URL]
[*][COLOR=Blue][Opencv Wiki ]("http://opencv.willowgarage.com/wiki/Welcome")[/COLOR]
[/LIST]

---

