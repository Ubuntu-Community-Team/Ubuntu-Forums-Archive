---
title: "firefox does not display the entire page source"
date: 2011-03-30
forum: General Help
---

### Post by tzoma on 2011-03-30
Hello everyone!

First of all I want to say that I'm new to Linux.
I am using Ubuntu 10.04 LL and i want to create a html page, in terminal mode, but firefox does not display it correctly.

i used this tutorial, [http://linuxcommand.org/wss0030.php](http://linuxcommand.org/wss0030.php) , but it seems that whatever i do, when i run the page with firefox (x@ubuntu:~/bin$ firefox page.html), the page displays the #!/bin/bash line, it doesn't interpret variables, reserved words, or any other special characters ( $, <<- ). I've tried to change the encoding in firefox from Unicode-8 to Unicode-32 but no luck :(

Any ideeas ?

Thanks a lot !

---

### Post by mcduck on 2011-03-30
Have you actually executed the script in the shell to generate the HTML page, or are you trying to open the script itself as web page?


The only way I can even think of which might result in the shebang showing in the browser's source view is if you tried viewing the script as a web page. Which is not going to work.

---

### Post by geek.de.nz on 2011-03-30
> **tzoma said:**
> Hello everyone!

First of all I want to say that I'm new to Linux.
I am using Ubuntu 10.04 LL and i want to create a html page, in terminal mode, but firefox does not display it correctly.

i used this tutorial, [http://linuxcommand.org/wss0030.php](http://linuxcommand.org/wss0030.php) , but it seems that whatever i do, when i run the page with firefox (x@ubuntu:~/bin$ firefox page.html), the page displays the #!/bin/bash line, it doesn't interpret variables, reserved words, or any other special characters ( $, <<- ). I've tried to change the encoding in firefox from Unicode-8 to Unicode-32 but no luck :(

Any ideeas ?

Thanks a lot !

Yeah, make sure you executed the script with 
```

./make_page > page.html

```If that gives you an error message or no valid html, try
```

chmod +x make_page

```Of course you need to be in the correct directory. Let us know the outputs if it still doesn't work. :D

---

### Post by tzoma on 2011-03-30
I have tried to execute the script to create a webpage using ./make_page > page.html . 
It replies : bash: ./make_page: No such file or directory. 

Inside the shell the script runs ok, it shows the HTML source, taking in consideration all the variables, special characters etc. However, when i try to generate a HTML page from the script, to use in firefox, i have the same problem.

@mcduck - the shebang appears when i try to run the script using firefox indeed. I know it's wrong - i just don't find the right "complier" to change my script into a webpage

---

### Post by geek.de.nz on 2011-03-30
You will have to use your file name of course.

---

### Post by tzoma on 2011-03-30
the filename for the page is page.html . The problem is that the "make_page" command is not to be found. What am I doing wrong here ?

---

### Post by mcduck on 2011-03-30
> **tzoma said:**
> I have tried to execute the script to create a webpage using ./make_page > page.html . 
It replies : bash: ./make_page: No such file or directory. 

Inside the shell the script runs ok, it shows the HTML source, taking in consideration all the variables, special characters etc. However, when i try to generate a HTML page from the script, to use in firefox, i have the same problem.

@mcduck - the shebang appears when i try to run the script using firefox indeed. I know it's wrong - i just don't find the right "complier" to change my script into a webpage

there is no "compiler", or actually the script itself would do that, yu just need to execute it.

So, make sure you are in the same directory where your script is, and that the script is set executable (chmod +x *nameofyourscript*), and then run it (./nameofyourscript > page.html)

That will create the html page for you, and you can then view it in the browser.

Anyway, if you are actually trying to learn how to create web pages in command line, instead of trying to learn how to create and use shells scripts, then all this is just overly complicated way of doing it, and you could simply type all that HTML code directly into the .html file instead. ;)

---

### Post by owiknowi on 2011-03-30
hi tzoma, i'm very much interested in your method of creating a web page.
when your problem is solved and you are willing of course, could you please let me know the benefits? are you for example just using a terminal without a gui?

i'm using bluefish most of the time but then a gui is required afaik.

btw. sorry not to be able to help because this is rather new to me...

regards, owiknowi

---

### Post by tzoma on 2011-03-30
Yes !

That was it. I took the "make_page" for granted - that's why it didn't work. 

Thank you for your support !

---

### Post by tzoma on 2011-03-30
@owiknowi 

I disabled the GUI in the boot up manager. I work in terminal mode because i want to learn linux without using the graphical interface - i guess it's a fad of mine. 

I use the [http://linuxcommand.org/index.php](http://linuxcommand.org/index.php) tutorial. It's a good way to learn the shell basics i think

I'm not familiar with apps under linux, but i think that you should use a dedicated editor for writing HTML - it's easier than to do it in shell, as mcduck also replied

A good day to you all

---

### Post by owiknowi on 2011-03-30
thanks tzoma. looks like a good way in order to really learn an os.

i've started with all the gui's since the '90s and now wanting less and less.
guess i'll end up with just a commandline in the end ;)

maybe this also can be useful for you:
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by mcduck on 2011-03-30
> **tzoma said:**
> @owiknowi 

I disabled the GUI in the boot up manager. I work in terminal mode because i want to learn linux without using the graphical interface - i guess it's a fad of mine. 

I use the [http://linuxcommand.org/index.php](http://linuxcommand.org/index.php) tutorial. It's a good way to learn the shell basics i think

I'm not familiar with apps under linux, but i think that you should use a dedicated editor for writing HTML - it's easier than to do it in shell, as mcduck also replied

A good day to you all

Well, learning is definitely a god enough reason to do this kind of stuff in a terminal. :D

Besides, there are some situations when shell scripting sure is a handy way to create web pages. I have a script that creates image gallery from all picture files in a directory. Much nicer way of doing such thing that writing all those img tags for hundreds of photographs by hand, and with Imagemagick you can handle resizing of the images and do all kinds of neat graphical things automatically at the same time...

Most of the time a normal text editor works better, of course. But for some types of tasks shell scripting can be a great tool even for web development. :)

---

