---
title: "skype webcam problem, missing file?"
date: 2011-01-01
forum: General Help
---

### Post by Mesqueeb on 2011-01-01
When I do

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

I get

ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

or

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

ERROR: ld.so: object '/usr/lib32/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.


However if I go to the file with gedit, it is empty/**nonexistent**....
Is this normal or does anyone wanne give me theirs? ^^
Thanks!

(Happy New Year!)

---

### Post by gordintoronto on 2011-01-01
There's a typing error in your command. Try copy/paste of this:
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

---

### Post by Mesqueeb on 2011-01-02
thank you, but...
if I use that code it's the same... I can call with it but when I press test in test webcam, the green light of my webcam flashes a bit, but eventually does nothing...

cheese works fine!

the object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded, and is ignored it would seem...

But actually** such a file seems non-existent **on my computer!
can anyone give me a copy of theirs? thanks!

-Mesqueeb

---

### Post by gordintoronto on 2011-01-02
Run Synaptic Package Manager and install lib32v4l-0, which contains the file.

---

### Post by Mesqueeb on 2011-01-03
It doesn't exist... I need to enable some extra locations for synaptics maybe?
Arrr!

Look: On this site that package is **only as amd64** version available... I don't know what that means, but I do know that it's the enemy of **i386**? And my skype seems to be i386... I couldn't install the lib32v4l-0 (amd64) thingy... Anyone has a i386 version, or just wants to share their '/usr/lib32/libv4l/v4l1compat.so' with me? ^^

-Mesqueeb

---

### Post by Mesqueeb on 2011-01-05
anyone has the file for me? ^^

---

### Post by no2498 on 2011-01-07
i do not know how to do it as i do not use skype
but you need to make the file for skype

---

### Post by Mesqueeb on 2011-01-14
anyone else can just copy the file and give it to me?

---

### Post by gradinaruvasile on 2011-01-19
open a terminal and type in:

```

sudo updatedb
/usr/lib/libv4l/v4l1compat.so

```

If there is no such file, do this:

```

sudo apt-get install libv4l-0

```

---

### Post by Mesqueeb on 2011-01-19
> **gradinaruvasile said:**
> open a terminal and type in:

```

sudo updatedb
/usr/lib/libv4l/v4l1compat.so

```

If there is no such file, do this:

```

sudo apt-get install libv4l-0

```

Okay, I did the first, it gave me a list with 2000 options, I don't know why. With the second line: /usr/lib/libv4l/v4l1compat.so it does nothing, it says bash no premission, I add sudo:
sudo /usr/lib/libv4l/v4l1compat.so
it says command not found

If I make the 2 lines into 1 line:
sudo updatedb /usr/lib/libv4l/v4l1compat.so
it says:

updatedb: &#12467;&#12510;&#12531;&#12489;&#12521;&#12452;&#12531;&#19978;&#12395;&#26399;&#24453;&#12375;&#12394;&#12356;&#12458;&#12506;&#12521;&#12531;&#12489;

= commandline upon don't aticipate (or something) "operando"

and "sudo apt-get install libv4l-0" seems to be already installed...

=S

---

### Post by gradinaruvasile on 2011-01-19
Damm. I wanted to say

locate /usr/lib/libv4l/v4l1compat.so

to see if the file in fact exists. The updatedb program re indexes the file list, should not have any output. Must be used with sudo.

---

### Post by Mesqueeb on 2011-01-19
Arrrrrr.... =(

i did:
sudo updatedb
&#8594; no output

then did:
locate /usr/lib/libv4l/v4l1compat.so
&#8594;and it just said: /usr/lib/libv4l/v4l1compat.so

So I was hoping, then I tried:
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

but still got:
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.


I can call, but no webcam. =( webcam in cheese = ok, when I press the "test" button in skype settings, my webcam light flashes a bit, but then does nothing...
arrrrrrrRR!!!! I am dooomed!!!! xD

-Mesqueeb

---

### Post by gradinaruvasile on 2011-01-20
> **Mesqueeb said:**
> Arrrrrr.... =(

i did:
sudo updatedb
&#8594; no output

then did:
locate /usr/lib/libv4l/v4l1compat.so
&#8594;and it just said: /usr/lib/libv4l/v4l1compat.so

So I was hoping, then I tried:
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

but still got:
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.


I can call, but no webcam. =( webcam in cheese = ok, when I press the "test" button in skype settings, my webcam light flashes a bit, but then does nothing...
arrrrrrrRR!!!! I am dooomed!!!! xD

-Mesqueeb

Try this:

```

sudo ldconfig

```

then proceed with the LD_PRELOAD command.

---

### Post by Mesqueeb on 2011-01-21
No, still the same problems as in Post #1. >,<
I am really thankful though! xD!!!!
Any other ideas?
arrrrr

-Mesqueeb

---

### Post by mciverza on 2011-01-21
> **Mesqueeb said:**
> 
So I was hoping, then I tried:
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

but still got:
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.


Notice that the /usr/lib/libv4l path does not match the /usr/lib32/libv4l path that you are getting an error on.

That might be (part of) the problem.

---

### Post by Mesqueeb on 2011-01-21
> **mciverza said:**
> Notice that the /usr/lib/libv4l path does not match the /usr/lib32/libv4l path that you are getting an error on.

That might be (part of) the problem.

Jup I thought so too, but even when trying the other command:

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

I get:

ERROR: ld.so: object '/usr/lib32/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

---

### Post by Mesqueeb on 2011-01-24
No thread yet has been able to help me, and I still have the problem......

When I press on test webcam in skype the webcam-light flashes 3 times, and then it won't work after all...

cheese works fine though...

Anyone knows what to do? THANKS!! ^^

-Mesqueeb

---

### Post by ajgreeny on 2011-01-24
You may already have tried this, but if not have a go at starting skype with this shell script:
```
#!/bin/bash
export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype

``` If you are running a 64 bit system, it may need to be changed slightly to take account of the differently named file to preload, but I'll leave you to research that.

If you've already tried this, just ignore me.

---

### Post by Mesqueeb on 2011-01-24
I get:


mesqueeb@Poliwhirl:~$ #!/bin/bash
mesqueeb@Poliwhirl:~$ export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
mesqueeb@Poliwhirl:~$ skype
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

---

### Post by ajgreeny on 2011-01-24
Have you used that as a shell script file?  It looks as if you ran the lines one at a time, which is not the way to do it.  Sorry if I mislead you, but I assumed you knew about script files.

Firstly check that you have the file I showed, /usr/lib32/libv4l/v4l1compat.so, and if it is there, copy, and paste those three lines of text into gedit and then save as skype.sh in your home.   Now make the file executable with ```
chmod +x skype.sh
```

Now try it by double clicking on it and choosing "run in terminal" which will give a chance to see any error messages that might be thrown up by the script.  If you have a 64 bit system you may need a different command for the preload line, but have a look at [https://help.ubuntu.com/community/Webcam/Troubleshooting](https://help.ubuntu.com/community/Webcam/Troubleshooting) if you've not already seen it, which does the same thing as my script in a slightly different way, and has the 64 bit details as well as 32 bit.

---

### Post by Mesqueeb on 2011-01-25
> **ajgreeny said:**
> Have you used that as a shell script file?  It looks as if you ran the lines one at a time, which is not the way to do it.  Sorry if I mislead you, but I assumed you knew about script files.

Firstly check that you have the file I showed, /usr/lib32/libv4l/v4l1compat.so, and if it is there, copy, and paste those three lines of text into gedit and then save as skype.sh in your home.   Now make the file executable with ```
chmod +x skype.sh
```

Now try it by double clicking on it and choosing "run in terminal" which will give a chance to see any error messages that might be thrown up by the script.  If you have a 64 bit system you may need a different command for the preload line, but have a look at [https://help.ubuntu.com/community/Webcam/Troubleshooting](https://help.ubuntu.com/community/Webcam/Troubleshooting) if you've not already seen it, which does the same thing as my script in a slightly different way, and has the 64 bit details as well as 32 bit.

Okay, I think I am closer to solving it:
The problem I have is that I went to usr/lib32/   and the only thing in there is:
* a folder: nvidea-173
* a folder: nvidea-current
* a folder: vdpau

nothing else! so no 'usr/lib32/libv4l/v4l1compat.so' !!!!!!

HOWEVER!
Your script said: '/usr/lib/libv4l/v4l2convert.so'  which is a different location. I went ahead and checked there and it was present! I tried the script anyway but I get:

ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

So I guess I should copy '/usr/lib/libv4l/v4l2convert.so' to a new folder I make in the lib32 folder and paste it like: '/usr/lib32/libv4l/v4l1compat.so', and it'll be solved? Or am I wrong?

-Mesqueeb

---

### Post by ajgreeny on 2011-01-25
Can we just check what architecture your system is with the command ```
uname -a
```in terminal.

---

### Post by Mesqueeb on 2011-01-25
> **ajgreeny said:**
> Can we just check what architecture your system is with the command ```
uname -a
```in terminal.

Linux Poliwhirl 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

You meant this?
I guess the i686 is the architecture? Yes no yes? ^^

---

### Post by ajgreeny on 2011-01-25
Yes, it means you have a 32 bit system.

However, it also perhaps means that the PRELOAD command that will sometimes work for difficult webcams, is not any use for yours with skype, and unfortunately I don't know where to go next.

---

### Post by Mesqueeb on 2011-01-25
> **ajgreeny said:**
> Yes, it means you have a 32 bit system.

However, it also perhaps means that the PRELOAD command that will sometimes work for difficult webcams, is not any use for yours with skype, and unfortunately I don't know where to go next.

Buy a new webcam? Which one do you recommend for ubuntu?

edit:
got it: [https://help.ubuntu.com/community/Webcam#Choosing](https://help.ubuntu.com/community/Webcam#Choosing) a Webcam

---

### Post by Mesqueeb on 2011-01-27
Okay, I threw the webcam away, and I plugged in a new webcam. Upon typing "cheese" in terminal get:
"libv4l2: error turning on stream: &#20837;&#21147;/&#20986;&#21147;&#12456;&#12521;&#12540;&#12391;&#12377;"
which means, in- and out-coming power error.

Thanks if anyone can help me!

-Mesqueeb

---

### Post by pwabrahams on 2011-02-05
I now have two different webcams attached, and I have the same problem with both of them.  So I doubt that the choice of webcam is the problem.

Here's what I get when I try the video test in Skype:

```
pwa@Asus-laptop:~$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype
Segmentation fault

```
I get the same with v4l2convert.

The maddening thing for me is that the video test actually worked a few weeks ago.  I update my system regularly, so I assume something in one of the updates killed my skype video.

---

### Post by pwabrahams on 2011-02-09
I just about gave up on finding the source of my problems with Skype video, so I tried a different approach.  I created another Kubuntu image from scratch in another partition on my hard drive -- and in that partition, the Skype video test works.  So now my problem is figuring out how to reinitialize my older Kubuntu image without losing the customizations I care about.  I determined that the problem is not in the dotfiles by creating another user and doing the test from there.  Same problem.  So just preserving /home will probably not be sufficient.

---

