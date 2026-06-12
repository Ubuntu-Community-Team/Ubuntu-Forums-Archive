---
title: "/usr/bin - how to access Python application without using it's extension ( .py ) ?"
date: 2009-09-02
forum: General Help
---

### Post by credobyte on 2009-09-02
```
/usr/bin/getip.py

```File is executable and I can use it as getip.py, however, I need a way to access it as getip ( without using it's extension ). Since aliases expire once the terminal windows is closed .. I've no idea how I could achieve this.

Anyone ?

---

### Post by Copernicus1234 on 2009-09-02
Yes, you can remove the .py extention and add a shebang at the top of your script:

```
#!/usr/bin/env python
```

Then ubuntu knows which program it should use to run your script.

---

### Post by credobyte on 2009-09-02
> **Copernicus1234 said:**
> Yes, you can remove the .py extention and add a shebang at the top of your script:

```
#!/usr/bin/env python
```Then ubuntu knows which program it should use to run your script.

That was the first line of my script, so .. it's there from the beginning. Still, [COLOR=RoyalBlue]bash: getip: command not found[/COLOR].

---

### Post by Cato2 on 2009-09-02
Try typing 'hash -r' in bash, and 'type getip' to see what the path is.  Also, double-check that the directory concerned is in your path.

And finally, chmod +x getip if not done already.

BTW I was in Riga only a couple of weeks ago - nice place :)

---

### Post by credobyte on 2009-09-02
> **Cato2 said:**
> Try typing 'hash -r' in bash, and 'type getip' to see what the path is.  Also, double-check that the directory concerned is in your path.

And finally, chmod +x getip if not done already.

BTW I was in Riga only a couple of weeks ago - nice place :)

It's executable, it's in /usr/bin, it's name is getip.py .. however, I still can't access it as getip.

```
dainis@ubuntu:~$ type getip.py
getip.py is /usr/bin/getip.py

dainis@ubuntu:/usr/bin$ ls -l | grep getip
-rwxr-xr-x 1 root   root         373 2009-09-02 20:22 getip.py
``````
dainis@ubuntu:~$ getip.py
Local IP address:    127.0.0.1
Public IP address:    94.30.182.129

dainis@ubuntu:~$ getip
Programma 'getip' &#353;obr&#299;d nav uzst&#257;d&#299;ta.  J&#363;s varat to uzst&#257;d&#299;t, ievadot:
sudo apt-get install knetfilter
bash: getip: command not found
```

-----------------------------------------------------------------------------------------

Problem solved .. Added a new alias to $HOME/.bashrc and everything works like a charm now :)

---

### Post by Cato2 on 2009-09-02
You need to rename it from getip.py to getip.  Try this:

<pre>
$ sudo -i
# cat >/usr/bin/getip
#!/usr/bin/env python

print "hello"

<Ctrl/D>
# exit
$ chmod +x /usr/bin/getip
$ getip
hello
</pre>

The message about knetfilter is worth noting - if you install that package it will overwrite your script.  I recommend you install yours in /usr/local/bin, which is automatically on every user's path and is guaranteed not to be overwritten by Ubuntu packages.

---

### Post by credobyte on 2009-09-02
> **Cato2 said:**
> You need to rename it from getip.py to getip.  Try this:

<pre>
$ sudo -i
# cat >/usr/bin/getip
#!/usr/bin/env python

print "hello"

<Ctrl/D>
# exit
$ chmod +x /usr/bin/getip
$ getip
hello
</pre>

The message about knetfilter is worth noting - if you install that package it will overwrite your script.  I recommend you install yours in /usr/local/bin, which is automatically on every user's path and is guaranteed not to be overwritten by Ubuntu packages.

Then what's the point of using .py extension ( if you can execute Python from a no-extension file ) ? 8-[
Regarding /usr/local/bin - thnx, will keep it in mind.

---

### Post by CatKiller on 2009-09-02
> **credobyte said:**
> Then what's the point of using .py extension ( if you can execute Python from a no-extension file ) ? 8-[

Using the filename as exclusive filetype metadata is just stupid. What the file *is* doesn't change when you change what it's *called*, does it? In a sensible system (AFAIK, anything but Windows) the filename/extension has no real bearing on what happens with that file. In GNU/Linux at least, filename extensions are to be read by the user, not by the computer.

EDIT: [Here]("http://arstechnica.com/apple/reviews/2001/08/metadata.ars")'s an old Ars Technica article on metadata that explains it better than I did.

---

### Post by Cato2 on 2009-09-02
> **credobyte said:**
> Then what's the point of using .py extension ( if you can execute Python from a no-extension file ) ? 8-[


Ummm, there is no point for this sort of script - just drop the extension.  Most text editors e.g. vim will look at the hashbang line (first line) to figure out it's a Python script for syntax highlighting.

The nice thing is that you can start with a shell script then rewrite into Python or even C without changing the name of the program.

---

### Post by credobyte on 2009-09-02
> **Cato2 said:**
> Ummm, there is no point for this sort of script - just drop the extension.  Most text editors e.g. vim will look at the hashbang line (first line) to figure out it's a Python script for syntax highlighting.

The nice thing is that you can start with a shell script then rewrite into Python or even C without changing the name of the program.

I don't think so ..

```
dainis@ubuntu:~/Programm&#275;šana/C++$ cat main
#include <iostream>

using namespace std;

int main(int argc, char *argv[])
{
    cout << "Hello, world!\n";
    return 0;
}
dainis@ubuntu:~/Programm&#275;šana/C++$ ls
main
dainis@ubuntu:~/Programm&#275;šana/C++$ g++ main -o app
main: file not recognized: File format not recognized
collect2: ld returned 1 exit status
```

---

### Post by Bachstelze on 2009-09-02
> **credobyte said:**
> I don't think so ..

```
dainis@ubuntu:~/Programm&#275;šana/C++$ cat main
#include <iostream>

using namespace std;

int main(int argc, char *argv[])
{
    cout << "Hello, world!\n";
    return 0;
}
dainis@ubuntu:~/Programm&#275;šana/C++$ ls
main
dainis@ubuntu:~/Programm&#275;šana/C++$ g++ main -o app
main: file not recognized: File format not recognized
collect2: ld returned 1 exit status
```

The name of the program, not the name of the source files...

---

### Post by credobyte on 2009-09-02
> **HymnToLife said:**
> The name of the program, not the name of the source files...

I meant it as a reply to someone else, who mentioned that we can start writing a Python application, then transform it bash script, or even, to a C program, without changing file name. As shown below, you can't do that ( C/C++ source needs an extension ).

---

### Post by Bachstelze on 2009-09-02
> **credobyte said:**
> I meant it as a reply to someone else, who mentioned that we can start writing a Python application, then transform it bash script, or even, to a C program, without changing file name. As shown below, you can't do that ( C/C++ source needs an extension ).

And I'm telling you a source file is not a program.

---

### Post by credobyte on 2009-09-02
> **HymnToLife said:**
> And I'm telling you a source file is not a program.

Then how would you make a C application without creating a source file ? Looks like someone got it wrong .. All I wanted to say is, you can't create a file "myapplication" and make it whatever you need ( Python, Java, C/C++, etc. ), without renaming it.

---

### Post by Bachstelze on 2009-09-02
> **credobyte said:**
> Then how would you make a C application without creating a source file ? Looks like someone got it wrong .. All I wanted to say is, you can't create a file "myapplication" and make it whatever you need ( Python, Java, C/C++, etc. ), without renaming it.

/facepalm

> **Cato2 said:**
> 
The nice thing is that you can start with a shell script then rewrite into Python or even C without changing **the name of the program**.

Got it? We're talking about the compiled program, not the source file.

---

### Post by credobyte on 2009-09-02
> **HymnToLife said:**
> /facepalm
 
Got it? We're talking about the compiled program, not the source file.
 
I don't know who's talking about what, but it's definitely far away from what I wanted to know. Thread reported!

---

### Post by falconindy on 2009-09-02
The point is that a script file without an extension can be written in any language, and the source will be interpreted properly because of the shebang. If there's no shebang (as in your C example) then you need to give the interpreter (or compiler) a little help.

```
g++ -x c++ main
```The above will "encourage" the compiler to interpret the file 'main' properly.

---

### Post by credobyte on 2009-09-02
> **falconindy said:**
> The point is that a script file without an extension can be written in any language, and the source will be interpreted properly because of the shebang. If there's no shebang (as in your C example) then you need to give the interpreter (or compiler) a little help.

```
g++ -x c++ main
```The above will "encourage" the compiler to interpret the file 'main' properly.

Thanks for the information :) Finally, someone showed how to do that.

---

