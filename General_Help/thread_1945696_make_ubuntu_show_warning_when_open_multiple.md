---
title: "make ubuntu show warning when open multiple"
date: 2012-03-23
forum: General Help
---

### Post by rezx on 2012-03-23
how can i make ubuntu show warning when open multiple files ??

---

### Post by Paddy Landau on 2012-03-24
How do you mean? Do you mean if you highlight more than one file in Nautilus to open them at the same time?

As far as I know, Nautilus does not have this option.

---

### Post by rezx on 2012-03-24
how come it didnt hve this option, how can i add it ??
when open multi files by mistake the system crash,
in winds when i open multi files it warn me that it may slow my pc, 
and that what ubunu need to add :)

---

### Post by Paddy Landau on 2012-03-25
I think you misunderstood me; sorry for being ambiguous.

I mean that Nautilus does not have the option to add a warning, as far as I know.

I am guessing you have an older computer if it crashes on opening multiple files. It used to happen to me, too, on an older computer. You'll just have to be careful not to do it.

---

### Post by WasMeHere on 2012-03-25
Welcome to the Ubuntu Forums, rezx,

In order to help, please let us know a bit more about your problem:

- I understand you are running lubuntu (according to the caption).
- What computer is it? (cpu, ram)
- What files are you trying to open?
- What program are you using to open them?

Have fun, not frustration, finding out :-)
Olle

---

### Post by Paddy Landau on 2012-03-25
> **Olle Wiklund said:**
> I understand you are running lubuntu
I'm sorry, I missed that. You would be using Thunar, not Nautilus. I don't know the options in Thunar.

---

### Post by Rodney9 on 2012-03-25
Lubuntu uses pcfman and as far as I know there is no option in it either.


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by rezx on 2012-03-25
thanks for ur reply and here is some information about my system
' You are using Ubuntu 10.04 LTS ' i hve normal cpu 3.2 as i can recall and 1g ram just burn one of them and left with 512MB, for the problem when i mark by mouse multi compressed files to extract my mouse some times make double click instead of one click so it click on the first command ' open ' so it take like forever to do that and the problem is bigger if  the files hve some pdf and mark it to move them and it click on open so imagine like 50 pdf files open at the same time.... i used to hve this problem on windows but it show box say its might slow my pc if i open all this files at once... 
just hope to be clear i work on ubuntu for a long time now this is the only problem i hve :)
its wonderfull system , but it hve to had this option if not how can i report to be added in the upcoming version...???

---

### Post by WasMeHere on 2012-03-25
> **rezx said:**
> thanks for ur reply and here is some information about my system
' You are using Ubuntu 10.04 LTS ' i hve normal cpu 3.2 as i can recall and 1g ram just burn one of them and left with 512MB, for the problem when i mark by mouse multi compressed files to extract my mouse some times make double click instead of one click so it click on the first command ' open ' so it take like forever to do that and the problem is bigger if  the files hve some pdf and mark it to move them and it click on open so imagine like 50 pdf files open at the same time.... i used to hve this problem on windows but it show box say its might slow my pc if i open all this files at once... 
just hope to be clear i work on ubuntu for a long time now this is the only problem i hve :)
its wonderfull system , but it hve to had this option if not how can i report to be added in the upcoming version...???
Thanks for posting data about your computer, It helps. But I'm confused about your version and flavour of Ubuntu. In the caption you have [lubuntu] and here you write Ubuntu 10.04 LTS.

Is it Ubuntu with gnome desktop or Lubuntu with LXDE? Or should I ask: What file browser do you run, nautilus or pcmanfm? Open the browser an click on
***Help -- About***
to get that information!

I don't know an easy way to get a warning message if several files are marked when you activate your command. Maybe you can call your program via a script, that counts the parameters, and if too many, it issues a warning like you are used to from Windows. But I know that it could be solved by using terminal window commands. Would you be interested in that. For many people, it is very efficient to use commands, so it is definitely worth learning.

---

### Post by WasMeHere on 2012-03-25
Maybe the following script can help you make an own script to call the archiver, move, evince or whatever program you want with a warning. Make a file called for example ***arg-counter*** and play with it.

```

#! /bin/bash

# Check for proper number of command line arguments.

E_BADARGS=65
EXPECTED_ARGS=3
echo "The command is $0 $*"
echo "There are $# parameters"

if [ $# -ne $EXPECTED_ARGS ]
then
  echo "Expected number of arguments is $EXPECTED_ARGS"
  exit $E_BADARGS
fi

```

---

### Post by WasMeHere on 2012-03-25
I had time and felt like making the following script. It should work for you. Let us call it pck and put it in the folder ~/pck.
```

#! /bin/bash

# Check for proper number of command line arguments and start an application

# by Olle Wiklund

# 1. Keep this script and links to it in an own folder, for example ~/pck
#
# 2. In the folder ~/pck, make a link from this script to the name (without
#    path) to the name of the program where you want to limit the number of
#    arguments, for example
#
#    ln pck file-roller
#
# 3. In your file browser right-click on a file with an extension you want to
#    be activated by this script. Select 'Properties' and 'Open with' and add
#    for the previous example
#
#    /home/$USER/pck/file-roller

#    Make that the default action by marking it with the 'radio-button' in
#    nautilus. It is a little different in other file browsers, but it should
#    work also in thunar and pcmanfm.

MAX_ARGS=1
E_BADARGS=65

# test
if [ $# -gt $MAX_ARGS ]
then
  echo "Maximum number of arguments is $MAX_ARGS"
  exit $E_BADARGS
elif [ $# == 0 ]
then
  $(basename $0)
else
  $(basename $0) "$*"
fi


```

---

### Post by rezx on 2012-03-26
i use ubuntu but i may mark lubuntu by mistake, my browser is 'Nautilus 2.30.1'

if any one work on windows will understand what i mean, any way its not a big deal the problem is in my mouse it make double click so it open files by mistake...
about the code is there any way to make the warning by   'gconf-editor'

writing program and need alot of work the reason i left windows cuz it need alot of work ' clean temp, virus, registry... and derangement... plus many many more....

if there is no an easy way can u ell me how to sed my problem to the ubuntu programer to add it in the next version :)

---

### Post by WasMeHere on 2012-03-27
> **rezx said:**
> i use ubuntu but i may mark lubuntu by mistake, my browser is 'Nautilus 2.30.1'

if any one work on windows will understand what i mean, any way its not a big deal the problem is in my mouse it make double click so it open files by mistake...
about the code is there any way to make the warning by   'gconf-editor'

writing program and need alot of work the reason i left windows cuz it need alot of work ' clean temp, virus, registry... and derangement... plus many many more....

if there is no an easy way can u ell me how to sed my problem to the ubuntu programer to add it in the next version :)
OK, good, you are running Nautilus. I don't know any built-in way to do what you want (neither directly in Nautilus nor by gconf-editor). [COLOR="Red"]Maybe someone else knows and can help you.[/COLOR]

But I made ***a script, that is doing what I [COLOR="RoyalBlue"]think[/COLOR] you want*** (see post #11). Did you try it? Or do you need help to get it installed?

[I]Edit: I think an easy way to ask the ubuntu programmers to add it in the next version is via
[[COLOR="RoyalBlue"]_http://brainstorm.ubuntu.com/_[/COLOR]]("http://brainstorm.ubuntu.com/")
Another maybe more efficient way is to get a launchpad account and ask from there.
[[COLOR="RoyalBlue"]_https://launchpad.net/launchpad_[/COLOR]]("https://launchpad.net/launchpad")[/I]

---

### Post by rezx on 2012-03-27
> **Olle Wiklund said:**
> I had time and felt like making the following script. It should work for you. Let us call it pck and put it in the folder ~/pck.
```

#! /bin/bash

# Check for proper number of command line arguments and start an application

# by Olle Wiklund

# 1. Keep this script and links to it in an own folder, for example ~/pck
#
# 2. In the folder ~/pck, make a link from this script to the name (without
#    path) to the name of the program where you want to limit the number of
#    arguments, for example
#
#    ln pck file-roller
#
# 3. In your file browser right-click on a file with an extension you want to
#    be activated by this script. Select 'Properties' and 'Open with' and add
#    for the previous example
#
#    /home/$USER/pck/file-roller

#    Make that the default action by marking it with the 'radio-button' in
#    nautilus. It is a little different in other file browsers, but it should
#    work also in thunar and pcmanfm.

MAX_ARGS=1
E_BADARGS=65

# test
if [ $# -gt $MAX_ARGS ]
then
  echo "Maximum number of arguments is $MAX_ARGS"
  exit $E_BADARGS
elif [ $# == 0 ]
then
  $(basename $0)
else
  $(basename $0) "$*"
fi


```

thanks for ur reply again, this is the script u mean, will it warn me when open multi files, and should i put it in every folder or on one folder if it shuold be in one folder, u may guide me how to install it and what is  ~/pck.

---

### Post by WasMeHere on 2012-03-27
> **rezx said:**
> thanks for ur reply again, this is the script u mean, will it warn me when open multi files, and should i put it in every folder or on one folder if it shuold be in one folder, u may guide me how to install it and what is  ~/pck.
Yes it is the script, and I will write the help partly in command line language.

[SIZE="3"]1. Script and links in an own folder[/SIZE]

~/pck is the folder pck in your home folder
~ is a brief notation for /home/$USER alias /home/rezx (if your local user name is rezx.

First start a terminal window (where you can run command lines) pressing the keys ***ctrl + alt + t*** at the same time. Type text commands with the keyboard and start running the command with the ***Enter*** key.

Change directory to your home folder with
```
cd
```
and make this folder
```
mkdir pck
``` and move inside this folder
```
cd pck
```

Now create the file pck inside that folder. Open the new file pck with the editor gedit
```
gedit pck &
```
Copy the text inside the code box from post #11 and paste it into the editor window. Then save the file. You can check that there is a file with the list command (lowercase Ls -lowercase L)
```
ls -l pck
``` and its content with the cat command ```
cat pck
```

Now make pck and links to it executable:
```
chmod ugo+x pck
```

The script, as it is now, will warn you writing

"Maximum number of arguments is 1" (MAX_ARGS=1, easy to change)

and exit if you call it from the command line. If you call it from Nautilus it will just exit without doing anything, and you have a chance to redo the selection. That can be changed later on. You should keep the script and make links to various names (the names of the programs to be used to open files) inside the folder ~/pck.

[SIZE="3"]2. Make links to the program names you want to protect from overloading.[/SIZE]

Next step is to decide which programs you are running often, so that you need this protection against opening several files. Let us list the files types you want to open, and then check what programs are called to open them. Feel free to add and subtract items from this list ;-)

```

ext - program
-------------
txt - gedit
odt - soffice
ods - soffice
odp - soffice
doc - soffice
xls - soffice
ppt - soffice
pdf - evince
jpg - eog
zip - file-roller
gz  - file-roller
mp3 - vlc
mp4 - vlc
wav - vlc

``` So link pck to these names (run the following commands) ```

ln pck gedit
ln pck soffice
ln pck evince
ln pck eog
ln pck file-roller
ln pck vlc

```

[SIZE="3"]3. Make Nautilus call the programs via this script[/SIZE]

In your file browser right-click on a file with an extension you want to be activated by this script. Select 'Properties' and 'Open with' and ***add*** (for the previous example) according to the following code boxes. Make that the ***default action*** by marking it with the 'radio-button' in Nautilus.

txt:
```
/home/rezx/pck/gedit %F
```

odt, ods, odp, doc, docx, xls, ppt:
```
/home/rezx/pck/soffice %F
```

pdf:
```
/home/rezx/pck/evince %F
```

jpg:
```
/home/rezx/pck/eog %F
```

zip, gz:
```
/home/rezx/pck/file-roller %F
```

mp3, mp4, wav:
```
/home/rezx/pck/vlc %F
```

You need to delete the original gedit to be able to select the new one as the default program to open the txt file type etc. Make that the default action by marking it with the 'radio-button' in Nautilus, otherwise it won't get activated when you double-click!

[SIZE="3"]4. Finally see the attached pictures in post #20[/SIZE]

Good luck :-)

---

### Post by rezx on 2012-03-28
wonderful, i make the steps but there is something i cant understand
in step no.2
where should i paste this ' ln pck gedit '
when i write it on terminal
ln: `pck': hard link not allowed for directory
and if  use cd pck
ln: accessing `pck': No such file or directory

what should do ?

---

### Post by WasMeHere on 2012-03-28
Run the following commands!
```
cd
``` and
```
cd pck
``` to get into the pck directory. And when you are there, create the file pck with gedit.

---

### Post by WasMeHere on 2012-03-28
Sorry I forgot one command, to make pck and links to it executable:
```
chmod ugo+x pck
```

---

### Post by rezx on 2012-03-28
im kind of lost after step 2

i hve 'open terminal here' so when be in pck just click ' open terminal here ' and there iam

then what should do ?
make a new file and paste this

ext - program
-------------
txt - gedit
odt - soffice
ods - soffice
odp - soffice
doc - soffice
xls - soffice
ppt - soffice
pdf - evince
jpg - eog
zip - file-roller
gz  - file-roller
mp3 - vlc
mp4 - vlc
wav - vlc

or this

ln pck gedit ln pck soffice ln pck evince ln pck eog ln pck file-roller ln pck vlc

and lets make it olny for text files use gedit whn i get the idea will add the other cuz i use
( movie player, open office, 7zip ... and movie plaer not vlc )

---

### Post by WasMeHere on 2012-03-28
I installed the system in my Ubuntu 10.04 LTS and it works now, but as usual, I had to do some debugging ;-) So when I select two or more txt files and press Enter, nothing happens. (Earlier all those files were opened.)

1. To make it clear how I intend the folder (directory) structure and the files, have a look at the attached picture ***pck.jpg*** of a nautilus window and a terminal window.

2. You need to use the explicit path to the application, not [COLOR="DarkOrange"]$USER[/COLOR] but your real user name ***rezx*** or whatever it is, similar to how I use ***olle*** and you must add a space and [COLOR="Red"]**%F**[/COLOR] afterwards to show that you want to call with several arguments instead of several calls with one argument each.
```
/home/[COLOR="DarkOrange"]rezx[/COLOR]/pck/gedit [COLOR="Red"]%F[/COLOR]
``` See the attached picture ***properties-add-program.jpg***

3. You need to delete the original ***gedit*** to be able to select the new one as the default program to open the ***txt*** file type.

See the attached picture ***properties-select-default.jpg***

---

### Post by WasMeHere on 2012-03-28
> **rezx said:**
> im kind of lost after step 2

i hve 'open terminal here' so when be in pck just click ' open terminal here ' and there iam

then what should do ?
make a new file and paste this

ext - program
-------------
txt - gedit
...

or this

ln pck gedit ln pck soffice ln pck evince ln pck eog ln pck file-roller ln pck vlc

and lets make it olny for text files use gedit whn i get the idea will add the other cuz i use
( movie player, open office, 7zip ... and movie plaer not vlc )
First, read carefully all my posts again. I have edited post #11 in order to get it correct (after the debugging). Look at the attached pictures in post #20.

Then, in the pck directory, run the command line
```
ln pck gedit
``` and then another line ```
ln pck soffice
```
etc for each program you want to protect from overloading.

For the next step, you should open Nautilus and change directory inside it so that you can see and select a text file. Right-click and select Properties. My attached screen-dump pictures may help, even if they are in Swedish.

---

### Post by WasMeHere on 2012-03-28
[SIZE="3"]Thunar might solve your problem[/SIZE]

An alternative file browser to Nautilus is ***Thunar***. It is not as powerful and has a smaller footprint than Nautilus, but I just observed, that it has a built-in property that may solve your problem without shell-scripts and tweaking. You can install it with the following command
```
apt-get install thunar
```
In order to open several files, you have to right-click and select 'Open'. If you have marked several files and press Enter, only one file is opened. I hope that this will also work with your mouse and/or touchpad clicking.

---

### Post by rezx on 2012-03-28
sudo apt-get install thunar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  exo-utils libexo-0.3-0 libexo-common libthunar-vfs-1-2 libxfce4util-bin
  libxfce4util-common libxfce4util4 libxfcegui4-4 libxfconf-0-2 thunar-data
  thunar-volman xfce-keyboard-shortcuts xfce4-panel xfconf
Suggested packages:
  thunar-archive-plugin thunar-media-tags-plugin
The following NEW packages will be installed:
  exo-utils libexo-0.3-0 libexo-common libthunar-vfs-1-2 libxfce4util-bin
  libxfce4util-common libxfce4util4 libxfcegui4-4 libxfconf-0-2 thunar
  thunar-data thunar-volman xfce-keyboard-shortcuts xfce4-panel xfconf
0 upgraded, 15 newly installed, 0 to remove and 411 not upgraded.
Need to get 10.9MB of archives.
After this operation, 24.4MB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libxfce4util-common 4.6.1-2ubuntu2 [53.4kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libxfce4util4 4.6.1-2ubuntu2 [51.6kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe libexo-common 0.3.106-1ubuntu2.1 [1,064kB]
1% [3 libexo-common 105kB/1,064kB 9%]                        3,857B/s 46min 20s

u r really assume, really... i'll tr to work the script and install Thunar, and will tell u what work best, u were so much helpful thanks for ur kindness

---

### Post by WasMeHere on 2012-03-28
You are welcome :-)

If Thunar does the job for you, keep it. Otherwise remove it with
```
apt-get remove thunar
``` to recover the space.

> i'll tr to work the script and install Thunar, and will tell u what work best
That's valuable for the Ubuntu Forum members :KS

---

### Post by rezx on 2012-03-28
sure, how can i rate ur help?

---

