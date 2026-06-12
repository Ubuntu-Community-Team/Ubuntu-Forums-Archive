---
title: "JMVision can't execute, even with permissions"
date: 2011-01-22
forum: General Help
---

### Post by grey1beard on 2011-01-22
Running 10.10 amd64 bit.
I've downloaded JMicroVision 1.2.7, and followed the install instructions, viz. extracted to my home folder, typed **chmod -R u+x JMicroVision-v127-linux** to get permissions to execute, and tried to launch from a terminal by typing **./JMVision**.
This produces the error - No such file or directory.

I've found an executable file with the same name in the plugins folder of the Extracted folder - **JMicroVision-v127-linux**, and it has execute permission, but if I double click on this, nothing happens.
Being a newbie, I'm now stuck, not sure what to do next.
Is the executable file in the wrong folder ?
What do I need to type in a terminal to try running it from there ?

In the web page, it advised typing **ldd JMVision** to find missing dependencies, but it can't find the file.
Do I get the correct result if I go to the plugins directory, then type the command ?

Bit over-cautious perhaps, but then that's me ;)

John

---

### Post by tredegar on 2011-01-22
It would have been helpful if you had told us where you downloaded this program from.
But I think I found it, after a bit of searching: [http://www.jmicrovision.com/download.htm](http://www.jmicrovision.com/download.htm)

> tried to launch from a terminal by typing ./JMVision.
This produces the error - No such file or directory.

It says in the installation instructions that you need to be "_In the directory of JMicroVision 1.2.7_ [snip]  type **./JMVision** in a Terminal screen."

So before you type **./JMVision** you need to **cd JMVisionDirectory** (or whatever it is really called) and *then* type **./JMVision**

The ./ means find the file JMVision in the _current_ directory.
To find out what directory you are in type **pwd** ("**p**rint **w**orking **d**irectory"), or pay attention to your terminal's prompt, which prints your working directory by default.

---

### Post by grey1beard on 2011-01-22
Thanks for your help.
I had already tried several permutations along those lines, but I have just spotted my errors - I'd put an s on the end of the file name first, then left the slash of the start at another attempt, so careless typing is my main problem.
I'll check this as solved when I get to the end of the process, not being that confident yet !
John

---

### Post by grey1beard on 2011-01-22
Extra carefully, I've moved forward, but found two files missing -
libpng.so.3 and libexpat.so.0 

In terminal I ran

> john@dragon:~$ sudo apt-get install libpng.so.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libpng.so.3
E: Couldn't find any package by regex 'libpng.so.3'
john@dragon:~$ sudo apt-get install libexpat.so.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libexpat.so.0
E: Couldn't find any package by regex 'libexpat.so.0''

so I should be grateful for some help.

John

---

### Post by tredegar on 2011-01-22
**libpng3** seems to have been replaced by **libpng12-0**, but you could try
```
sudo apt-get install libpng3
```

**libexpat.so.0** seems to have been replaced by **libexpat.so.1** but you could try
```
sudo apt-get install libexpat1
```

Now, to fix up the absence of libexpat.so.0 do this:
```
sudo  ln  -sT  /usr/lib/libexpat.so.1  /usr/lib/libexpat.so.0
```

Which makes a link, so when the program goes looking for **/usr/lib/libexpat.so.0** it thinks it has found it (right name) but really it gets **/usr/lib/libexpat.so.1** which will probably work OK, but there's only one way to find out.

---

### Post by grey1beard on 2011-01-22
> libpng3 is already the newest version
> libexpat1 is already the newest version

so I copied your last command to link so.1 to so.0 ,and got my command line back instantly, so I assume that was OK.
I then tried to open the program in terminal, and got

> ./JMVision: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

I went to the /usr/lib folder and found the libpng.so.3 file with a X on it, so I looked at the properties and found -
Type:        Link (broken) (inode/symlink)
Link target: libpng12.s.0

and a "File Search" for this target said file not found.

John

---

### Post by tredegar on 2011-01-22
> I went to the /usr/lib folder and found the libpng.so.3 file with a X on it, so I looked at the properties and found -
Type: Link (broken) (inode/symlink)
Link target: libpng12.s.0

OK, this looks like it is an "Ubuntu is broken" bug.

The file **/usr/lib/libpng.so.3** is a link pointing to **/usr/lib/libpng12.so**
But the file **libpng12.so** is not in **/usr/lib/** it is in plain old **/lib/** and it *is itself* a link, pointing to **/lib/libpng12.so.0.42.0**

So this should fix it
```
sudo  rm  /usr/lib/libpng.so.3
sudo  ln  -sT    /lib/libpng12.so.0.42.0  /usr/lib/libpng.so.3
```
Remember, you are running those commands as root. TRIPLE check your spelling before pressing <RETURN>

Now when you look at the file **/usr/lib/libpng.so.3** with your file manager, you will see the link is no longer broken.

You can confirm this with ```
ls -l /usr/lib/libpng.so.3
```

Perhaps your program will run now.

---

### Post by grey1beard on 2011-01-22
I've posted my last terminal commands, but the link is still broken :(

> john@dragon:~$ sudo  ln  -sT    /lib/libpng12.so.0.42.0  /usr/lib/libpng.so.3
john@dragon:~$ ls -l /usr/lib/libpng.so.3
lrwxrwxrwx 1 root root 23 2011-01-22 17:26 /usr/lib/libpng.so.3 -> /lib/libpng12.so.0.42.0
john@dragon:~$ cd JMicroVision-v127-linux
john@dragon:~/JMicroVision-v127-linux$ ./JMVision
./JMVision: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory


John

---

### Post by grey1beard on 2011-01-22
Am I just trying to open it from the wrong place ?
Checking the "properties/open with" for the executable file, it says "no application selected".
Is this the/another problem ?
John

---

### Post by grey1beard on 2011-01-22
Just found that /lib/libpng12.so.0.42.0 doesn't exist.
There is a file /lib/libpng12.so.0.44.0 however.

John

---

### Post by tredegar on 2011-01-22
> lrwxrwxrwx 1 root root 23 2011-01-22 17:26 /usr/lib/libpng.so.3 -> /lib/libpng12.so.0.42.0

./JMVision: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory 

The link is there, so now I am stuck. It is possible that JMVision is looking for it in the wrong place (ie not in /usr/lib )

But it is worth running 
```
sudo ldconfig
```
to reconfigure the dynamic linker run-time bindings.

And then try ./JMVision again.

---

### Post by tredegar on 2011-01-23
I finally got your program to run, (though I have no idea what it is supposed to do.)

Please open a terminal, run the commands in [COLOR="Red"]red[/COLOR] and post the output as I have done:
```
tred@vaio2:~$ [COLOR="Red"]sudo updatedb[/COLOR]
[sudo] password for tred: 
tred@vaio2:~$ [COLOR="Red"]ls -l $(locate libexpat.so.0)[/COLOR]
lrwxrwxrwx 1 root root 18 2011-01-23 15:50 /lib/libexpat.so.0 -> /lib/libexpat.so.1
tred@vaio2:~$ [COLOR="Red"]ls -l $(locate libpng.so.3)[/COLOR]
lrwxrwxrwx 1 root root 23 2011-01-22 15:50 /usr/lib/libpng.so.3 -> /lib/libpng12.so.0.42.0
tred@vaio2:~$ 
```
then I should be able to tell you how to fix the links up properly.

---

### Post by grey1beard on 2011-01-23
Hi tredegar
As per request - 
> john@dragon:~$ sudo updatedb
[sudo] password for john: 
john@dragon:~$ ls -l $(locate libexpat.so.0)
lrwxrwxrwx 1 root root 17 2011-01-22 22:13 /lib/libexpat.so.0 -> libexpat.so.1.5.2
john@dragon:~$ ls -l $(locate libpng.so.3)
lrwxrwxrwx 1 root root 13 2011-01-22 22:09 /usr/lib/libpng.so.3 -> libpng12.so.0
john@dragon:~$ 


John
PS the first location is in green, but the second is in red

---

### Post by tredegar on 2011-01-23
Ok.
Try this 
```
sudo  rm  /usr/lib/libpng.so.3 
sudo ln   -sT   /lib/libpng12.so.0.42.0    /usr/lib/libpng.so.3
sudo ldconfig
cd ~/JMicroVision-v127-linux
./JMVision
```

If that fails, please repeat the steps in post #12

If you click "Go Advanced" instead of Submit reply, you can use code tags, change colours, preview your post's formatting etc.

---

### Post by grey1beard on 2011-01-23
I'm afraid it failed, so do I carry out #12 starting from the john@dragon:~/JMicroVision-v127-linux$ directory, or my home directory ?

Thanks 
John

---

### Post by grey1beard on 2011-01-23
Just  did
> john@dragon:~$ ls -l $(locate libpng.so.3)
ls: cannot access /usr/lib/libpng.so.3: No such file or directory
john@dragon:~$ 

We deleted it in #14 ?
John

---

### Post by tredegar on 2011-01-23
> We deleted it in #14 ?
Yes.
And then you recreated it with 
```
sudo ln   -sT   /lib/libpng12.so.0.42.0    /usr/lib/libpng.so.3
```
locate will not find newly created files or notice recently deleted ones until you have done a
```
sudo updatedb
```
Normally that happens automatically, but only once a day.

Meanwhile just follow the steps in #12 all over again.

---

### Post by grey1beard on 2011-01-23
As requested - 

john@dragon:~$ sudo updatedb
john@dragon:~$ ls -l $(locate libexpat.so.0)
lrwxrwxrwx 1 root root 17 2011-01-22 22:13 [COLOR="Cyan"]/lib/libexpat.so.0[/COLOR] -> libexpat.so.1.5.2
john@dragon:~$ ls -l $(locate libpng.so.3)
total 99960
-rw-r--r--  1 john john   349249 2011-01-03 14:01 [COLOR="Red"]2010_0817_RT73_Linux_STA_v1.1.0.4.tar.bz2[/COLOR]
-rw-r--r--  1 john john    52161 2010-11-05 21:17 AutoSave_Untitled.skp
-rwxr-xr-x  1 john john    28360 2008-12-15 09:47 [COLOR="Lime"]compiz-check[/COLOR]
drwxr-xr-x  3 john john     4096 2011-01-22 11:04 [COLOR="DeepSkyBlue"]Desktop[/COLOR]
drwxr-xr-x  2 john john     4096 2011-01-11 21:52 [COLOR="DeepSkyBlue"]Documents[/COLOR]
drwxr-xr-x  3 john john     4096 2011-01-22 11:03 [COLOR="DeepSkyBlue"]Downloads[/COLOR]
drwxr-xr-x  4 john john     4096 2010-12-01 14:20 [COLOR="DeepSkyBlue"]emc2[/COLOR]
-rwxr-xr-x  1 john john      234 2010-12-01 14:24 [COLOR="Lime"]emc2.desktop[/COLOR]
-rw-r--r--  1 john john      179 2010-10-15 09:55 examples.desktop
drwxr-xr-x  4 john john     4096 2010-12-14 12:31 [COLOR="DeepSkyBlue"]get_iplayer-2.78[/COLOR]
-rw-r--r--  1 john john   194080 2010-12-14 12:13 [COLOR="DeepSkyBlue"][COLOR="Red"]get_iplayer-2.78.tar.gz[/COLOR][/COLOR]
-rw-r--r--  1 root root 32950070 2010-11-02 21:21 [COLOR="Red"]googleearth_5.2.1.1588+0.5.7-1_amd64.deb[/COLOR]
-rw-r--r--  1 root root 31406473 2010-09-02 17:30 GoogleEarthLinux.bin
drwxr-xr-x  5 john john     4096 2008-03-01 16:03 J[COLOR="DeepSkyBlue"]MicroVision-v127-linux[/COLOR]
-rw-r--r--  1 john john 32205955 2011-01-22 10:25 [COLOR="Red"]JMicroVision-v127-linux.tar.gz[/COLOR]
drwxr-xr-x  2 john john     4096 2010-10-15 10:04 [COLOR="DeepSkyBlue"]Music[/COLOR]
drwxr-xr-x  3 john john     4096 2010-12-20 16:07 [COLOR="DeepSkyBlue"]Pictures[/COLOR]
drwxr-xr-x  2 john john     4096 2010-10-15 10:04 [COLOR="DeepSkyBlue"]Public[/COLOR]
drwxr-xr-x  4 john john     4096 2010-12-18 18:12 [COLOR="DeepSkyBlue"]RHONDA_V24_PC[/COLOR]
-rw-r--r--  1 john john  1682450 2010-11-08 14:21 [COLOR="Red"]RHONDA_V24_PC.zip[/COLOR]
drwxr-xr-x 12 john john     4096 2010-11-21 23:10 [COLOR="DeepSkyBlue"]sane-backends-1.0.16[/COLOR]
-rw-r--r--  1 john john  3409799 2010-11-20 20:35 [COLOR="Red"]sane-backends-1.0.16.tar.gz[/COLOR]
drwxr-xr-x  2 john john     4096 2010-11-21 21:20 [COLOR="DeepSkyBlue"]sanity[/COLOR]
drwxr-xr-x  2 john john     4096 2010-10-15 10:04 [COLOR="DeepSkyBlue"]Templates[/COLOR]
drwxr-xr-x  2 john john     4096 2010-10-15 10:04 [COLOR="DeepSkyBlue"]Videos[/COLOR]
john@dragon:~$

John

---

### Post by tredegar on 2011-01-23
Thank you.

When you gave this command **ls -l $(locate libpng.so.3)** the locate didn't find the file, so the command resolved to just **ls -l** which listed your home dir, which is OK.

So we need to create the link for **libpng.so.3** like this
```
sudo ln -sT  /lib/libpng12.so.0.42.0    /usr/lib/libpng.so.3
sudo ldconfig
```
Then try ```
cd   ~/JMicroVision-v127-linux
./JMVision
```

Do you know you can copy & paste from this browser window directly into a terminal?

[INDENT][LIST]
[*]Open a terminal window, next to this one.

[*]Highlight the text in your browser that you want pasting into the terminal.

[*]L-Click on the terminal window to bring it into focus ("to the front").

[*]Middle-click in the terminal window.

[*]The text will be pasted. You may have to press RETURN to have it executed.
[/LIST]
[/INDENT]
Earlier you asked > so do I carry out #12 starting from the john@dragon:~/JMicroVision-v127-linux$ directory, or my home directory ?
The answer is that it does not matter, because all the commands I gave you referencing files carefully referenced the files by their *full path names*.

A full path name begins with the [COLOR="Red"]/[/COLOR] character like **ls [COLOR="Red"]/[/COLOR]lib/libpng12.so.0.42.0**

A *relative* path looks like this with no leading [COLOR="Red"]/[/COLOR]
```
cd JMicroVision-v127-linux
```
That just means "look in the current directory for the directory **JMicroVision-v127-linux** and move into it"
If you are in **/home/john** that will work because the directory **/home/john/JMicroVision-v127-linux** exists.

If you are somewhere else and give that command it will fail with **JMicroVision-v127-linux - not found**

"Not found" doesn't mean "doesn't exist anywhere" it means "Not found in the current directory".

To find out your current directory, look at your bash prompt, or give the command **pwd** (**p**rint **w**orking **d**irectory)

Linux isn't windows, and your life would be easier (and this problem already solved) if you learned a bit about the command line.
Enough off-topicness. Try making that link.

Hope it works for you this time.

---

### Post by grey1beard on 2011-01-23
Here you go -
> john@dragon:~$ sudo ln -sT  /lib/libpng12.so.0.42.0    /usr/lib/libpng.so.3
[sudo] password for john: 
john@dragon:~$ sudo ldconfig
john@dragon:~$ cd   ~/JMicroVision-v127-linux
john@dragon:~/JMicroVision-v127-linux$ ./JMVision
./JMVision: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory
john@dragon:~/JMicroVision-v127-linux$

Thanks for your continued help and the extras. 
One of the first things I learned as a 72 year old, with about twenty years of using Windows, was that starting to change over to Ubuntu last October might take a little while, and the safest way to follow instructions was to "copy/paste."
Earlier typos have only reinforced that lesson !

John

---

### Post by tredegar on 2011-01-23
Ok, it is still not working on your PC, but it is on mine. Your links are still wrong, but this is fixable.

It would be helpful to me if I can see the commands you have executed.

If you type **history** into a terminal you'll see the commands you have recently used. Please copy & paste the relevant bits here. I'll make of it what I can.

Please don't use "Quote" when posting code (command line stuff) - instead use "Code" (**#** Icon) from the Advanced menu. That way I can see if you have missed out spaces etc. in the commands. Sometimes this matters. Colours do not matter, unless you need them for emphasis.

**./JMVision **runs fine on my PC, once I had the links set up properly. So this is an "easily" solvable problem. Somehow, I think, you are not following my advice literally and to the letter.

72y is nothing, I have 85y olds happily using linux, but they trust me and I tend to ask them to "Share my desktop" with me, and then I just fix it up. It's a matter of trust, and I understand that you should not do that with me, an unknown entity on the big bad interweb.

Just persevere. But it's time for food & bed for me, as I have a very busy week ahead.

Go ahead and post, remember that I might be slow to reply, but we'll get there eventually.

---

### Post by grey1beard on 2011-01-23
```
sudo updatedb
locate libpng.so
locate libpng |grep '\.so'
cd /usr/lib
sudo ln -s libpng12.so.0 libpng.so.3
locate libexpat
cd /lib
sudo ln -s libexpat.so.1.5.2 libexpat.so.0
cd /usr/lib
sudo updatedb
ls -l $(locate libexpat.so.0)
ls -l $(locate libpng.so.3)
sudo  rm  /usr/lib/libpng.so.3
sudo ln   -sT   /lib/libpng12.so.0.42.0    /usr/lib/libpng.so.3
sudo ldconfig
cd ~/JMicroVision-v127-linux
./JMVision
cd ~
ls -l $(locate libpng.so.3)
sudo updatedb
ls -l $(locate libexpat.so.0)
ls -l $(locate libpng.so.3)
sudo updatedb
ls -l $(locate libexpat.so.0)
ls -l $(locate libpng.so.3)
sudo ln -sT  /lib/libpng12.so.0.42.0    /usr/lib/libpng.so.3
sudo ldconfig
cd   ~/JMicroVision-v127-linux
./JMVision
 

```

I think this is the history from #12 onwards.
Regards
John

---

### Post by tredegar on 2011-01-24
Thank you.

This is all in a muddle.

Please copy and paste the following commands, then post the results (along with the commands, ie just copy & paste the terminal screen, and please don't forget the # CODE tags)

```
sudo updatedb
ls -l $(locate libpng12.so)
ls -l $(locate libpng.so)
ls -l $(locate libexpat.so)
```

Then I can take another look at how your links are set up.

---

### Post by grey1beard on 2011-01-24
Good Morning tredegar, and thanks.
John

```
john@dragon:~$ sudo updatedb
[sudo] password for john: 
john@dragon:~$ ls -l $(locate libpng12.so)
lrwxrwxrwx 1 root root     13 2010-11-02 19:40 /lib32/libpng12.so -> libpng12.so.0
lrwxrwxrwx 1 root root     18 2010-11-02 19:40 /lib32/libpng12.so.0 -> libpng12.so.0.44.0
-rw-r--r-- 1 root root 145260 2010-06-29 10:58 /lib32/libpng12.so.0.44.0
lrwxrwxrwx 1 root root     18 2010-10-15 09:45 /lib/libpng12.so.0 -> libpng12.so.0.44.0
-rw-r--r-- 1 root root 158736 2010-06-29 12:30 /lib/libpng12.so.0.44.0
lrwxrwxrwx 1 root root     20 2010-11-02 19:40 /usr/lib32/libpng12.so -> /lib32/libpng12.so.0
lrwxrwxrwx 1 root root      9 2010-11-02 19:45 /usr/lib32/libpng12.so.0 -> libpng.so
john@dragon:~$ ls -l $(locate libpng.so)
lrwxrwxrwx 1 root root    20 2010-11-02 19:40 /usr/lib32/libpng.so -> /lib32/libpng12.so.0
-rw-r--r-- 1 root root 14784 2010-10-22 09:03 /usr/lib/compiz/libpng.so
john@dragon:~$ ls -l $(locate libexpat.so)
lrwxrwxrwx 1 root root     13 2010-11-02 19:40 /lib32/libexpat.so -> libexpat.so.1
lrwxrwxrwx 1 root root     17 2010-11-02 19:40 /lib32/libexpat.so.1 -> libexpat.so.1.5.2
-rw-r--r-- 1 root root 157064 2010-01-19 16:49 /lib32/libexpat.so.1.5.2
lrwxrwxrwx 1 root root     17 2011-01-22 22:13 /lib/libexpat.so.0 -> libexpat.so.1.5.2
lrwxrwxrwx 1 root root     17 2010-10-15 09:45 /lib/libexpat.so.1 -> libexpat.so.1.5.2
-rw-r--r-- 1 root root 165960 2010-01-19 17:07 /lib/libexpat.so.1.5.2
john@dragon:~$ 

```

---

### Post by tredegar on 2011-01-24
Thank you. Code tags too!

I see **/lib32/** and wonder ....  are you running a 64-bit AMD linux?
I know the answer is "yes" because that was the first line of your first post, but I had forgotten in the intervening time.

Anyway, the links you are missing can be created with this:

```
sudo ln -sT /lib32/libpng12.so /lib32/libpng.so.3
sudo ln -sT /lib32/libexpat.so /lib32/libexpat.so.0
sudo ldconfig
```

We might as well sort out the 64-bit libraries as well:
```
sudo ln -sT /lib/libpng12.so.0  /lib/libpng.so.3
sudo ldconfig
```
Note: **libexpat.so.o** was already correctly linked on the 22-1-2011 (You did that one right!)

Please copy, paste & execute the above commands exactly as they are. Do not be tempted to use any clever "short cuts".

But this may still not work, because the JMVision thing is 32-bits (because it runs on my PC), was apparently written 5y ago, and is probably going to look for the libraries somewhere other than **/lib32/** like **/lib/** or **/usr/lib/**. Or maybe the 64-bit libraries will work, I have no idea, as I am happy with my 32-bits.

Worth a try though.

If it doesn't work, I do not know how to adjust the library paths JMVision is searching.
If we put any links to the 32-bit libraries in **/lib/** (where JMV may be looking for them) then some other 64-bit applications will be broken, so don't even think about it.

If it fails and you *really* want this program, then make room on your disk for another partition and install 32-bit ubuntu there. Grub2 will let you choose which to boot.

Unless you are running massive databases, crunching huge numbers or need >4GB RAM, then there is probably no need for a 64-bit kernel, and a 32-bit one will run just fine, maybe even better ("bigger" isn't _always_ "better").

Let us know how you get on.

---

### Post by grey1beard on 2011-01-24
```
sudu ldconfig
``` 
I presume this is a typo for sudo ldconfig ?
I copy/pasted it and got the expected result !
John

---

### Post by tredegar on 2011-01-24
Yes, it's a typo.

Sorry. I hate sudo, I'm an old-fashioned **su** person so my lazy fingers find the "U" faster, and sometimes inappropriately.

Try again. I'll edit the post in case someone else follows it.

---

### Post by grey1beard on 2011-01-24
You've done it !
Many, many thanks for your patience.

As you had wondered at my need for the program, I can only point you to [www.cnczone.com](www.cnczone.com), where a long running thread(>4300 posts and rising) on the subject of Epoxy/Granite machine frames has welcomed my posting of a link to this piece of software.
I'm fairly sure it's going to prove to be extremely useful to most of the participants, so it was somewhat ironic that I couldn't install it myself.

Thanks again,
John

---

### Post by tredegar on 2011-01-24
Pleased you have it working (because I can now remove it from my PC!).

I'd be interested to know if it is the 64-bit links that worked or the /lib-32/ ones, but perhaps it doesn't really matter.

Best wishes.

---

