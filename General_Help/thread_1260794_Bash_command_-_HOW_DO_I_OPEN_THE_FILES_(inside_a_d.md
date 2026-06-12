---
title: "Bash command - HOW DO I OPEN THE FILES (inside a directory) ???"
date: 2009-09-08
forum: General Help
---

### Post by nomnex on 2009-09-08
This is a simple one.

I am learning Bash basic commands.
When I am browsing a directory, ls -lh, how do I open the files inside of it?
I don't want to use the 'less' command, I want a simple way to open and see what's in there (.pdf, .jpg, .odt, .wmv, etc) and of course, after I close the file, I expect to return to the bash window.

How can I do that? Thanks

---

### Post by amac777 on 2009-09-08
The command you will use to open the file will depend according to what kind of file it is:

Here are some common ones:

```

eog pic.jpg
gedit file.txt
totem movie.avi
evince file.pdf
ooffice document.doc

```

---

### Post by PaulWhipp on 2009-09-08
There are lots of ways to do this depending upon your goal.

The 'cat' command displays the content of the file on stdout so is often handy in bash scripts. 'head' and 'tail' can be handy when you just want to get a hint of the file contents.

'grep' is cool for finding files with particular stuff in them (-l makes it print just the filename).

'sed' is cool for changing the files based upon their existing content.

I generally favour find over ls because its easier to handle its output.

For example:

```

~ $ # invoke head on each file in websites/cfg folder with http in its content
~ $ find websites/cfg  -maxdepth 1 -type f | xargs grep -l "http" | xargs head

```

To get quick and slightly more friendly output, you can use a loop:

```

~ $ find . -maxdepth 1 -type f | xargs grep -l "http" | while read file_name; do echo "==${file_name}"==; head ${file_name}; echo ""; done


```

Hopefully you can vary this to get what you are after ;)

---

### Post by credobyte on 2009-09-08
```
open mystery.pdf
open unknown.mp3
open question.doc

```

Files will be opened with their default applications ( with 'default' I mean, #1 in Open with ).

---

### Post by nomnex on 2009-09-08
Thanks to all for the support

@ amak777

That's quite easy, but I must remember the name of all the applications. Anyway, thanks a bunch, I can use it straight away. It works.

@ PaulWhipp

It is too advanced for me. I said basic commands. I will get back to your post later. However I ask for an easy way to open various files in folders using bash instead of a GUI. Grep, is for seaching file. Don't really follow. But thanks.

@ credobyte

That would be the best - simple yes! but it does not work. am I doing something wrong?

```
mtpc03@mtpc03-laptop:~/Desktop$ open IKA-1.pdf
Couldnt get a file descriptor referring to the console
mtpc03@mtpc03-laptop:~/Desktop$ 

```

---

### Post by manuelgsc on 2009-09-08
If you're using gnome you can use gnome-open:

```

gnome-open pepe.txt
gnome-open sheet.xls
gnome-open usecase.pdf
```

---

### Post by nomnex on 2009-09-08
Thanks that works now!

Just a precision, using gnome-open + file name will always use the default application

let's say sample.mpg (video) default player Ubuntu is Movie player, so if I

```
gnome-open sample.mpg
```It will play the file using Movie player. Now if I want to open the same file with SMPlayer, then what

```
SMPlayer sample.mpg
```as explained in the first answer?

Thanks

---

### Post by manuelgsc on 2009-09-08
> **nomnex said:**
> Now if I want to open the same file with SMPlayer, then what

```
SMPlayer sample.mpg
```as explained in the first answer?

Thanks


I guess, it depends on the SMPlayer command line syntax.

---

### Post by andrew.46 on 2009-09-08
Hi nomnex,

> **nomnex said:**
>  Now if I want to open the same file with SMPlayer, then what

```
SMPlayer sample.mpg
```as explained in the first answer?


If you are interested in running from a terminal you would be better to simply run:

```
mplayer sample.mpg
```

rather than open the gui for MPlayer from within a terminal. Hopefully that makes sense :-).

Andrew

---

### Post by nomnex on 2009-09-08
I have tried, that did not work

```
mtpc03@mtpc03-laptop:~/Videos/MediaLink/X$ SMPlayer 001.wmv
bash: SMPlayer: command not found
mtpc03@mtpc03-laptop:~/Videos/MediaLink/X$ 
```

also with Mplayer

```
mtpc03@mtpc03-laptop:~/Videos/MediaLink/X$ MPlayer 001.wmv
bash: MPlayer: command not found
```

@Andrew
>rather than open a gui for MPlayer from a terminal. Hopefully that makes sense

what do you mean? is SMplayer ONLY a gui? doesn'it offer more functions/settings?

---

### Post by nomnex on 2009-09-08
OMG, I used captial letters! smplayer/mplayer....

---

### Post by nothingspecial on 2009-09-08
smplayer is a gui for mplayer.

If you just want to listen to a tune or watch a vid from the shell there`s no need to launch smplayer as you are using the command line.

---

### Post by nomnex on 2009-09-08
I see, thanks to everyone for your support. I close the thread now.

---

### Post by andrew.46 on 2009-09-08
Hi nomnex,

> **nomnex said:**
> what do you mean? is SMplayer ONLY a gui? doesn'it offer more functions/settings?

Well I would never actually call SMPlayer *only* a gui as it goes over and beyond what you would expect from a front-end. But all the commands and functions that it uses can be duplicated from the commandline, but this will never be as easy as using SMPlayer itself :-).

Andrew

---

### Post by nomnex on 2009-09-08
Hi back Andrew.46 and thanks for the precision. If you happen to know a guide/link to use MPlayer from complete beginner to advance, I am glad to read it. And let me ask, even if it is out of topic, don't SMPlayer comes with additional codecs pack (as I does under Windows) when I install it using Synaptic?

---

### Post by andrew.46 on 2009-09-08
Hi nomnex,

> **nomnex said:**
> Hi back Andrew.46 and thanks for the precision.

Oh no, have I come across as a little obsessive and picky again :).

> If you happen to know a guide/link to use MPlayer from complete beginner to advance, I am glad to read it. 

I will have to admit that guides for the complete beginner are a little thin on the ground. The iconic place to begin though is probably the MPlayer html documentation which can be found here:

MPlayer - The Movie Player
[http://www.mplayerhq.hu/DOCS/HTML/en/index.html](http://www.mplayerhq.hu/DOCS/HTML/en/index.html)

This, like much of the MPlayer world is aimed at the svn MPlayer. If you are interested I have written a guide for installation of the svn MPlayer here:

HowTo: Install the very latest MPlayer under Jaunty Jackalope
[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

and while I am pimping my own guides, an advanced user guide here:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

but I suspect you will find that beginner's guides are not all that easily found and you may have to enlist my 2 best friends Trial and Error :).

> And let me ask, even if it is out of topic, don't SMPlayer comes with additional codecs pack (as I does under Windows) when I install it using Synaptic?

No it does not unfortunately. But codecs for MPlayer can be found in the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository as w32codecs or a substantially lesser package for 64bit users.

All the best,

Andrew

---

### Post by nomnex on 2009-09-08
[quote=andrew.46]Oh no, have I come across as a little obsessive and picky again.[/quote]

Indeed :)

Links and info much appreciated. See you & Thanks.

---

