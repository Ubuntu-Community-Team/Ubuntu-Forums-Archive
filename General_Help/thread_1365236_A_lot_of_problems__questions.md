---
title: "A lot of problems / questions"
date: 2009-12-27
forum: General Help
---

### Post by Kempen on 2009-12-27
I'm in a bit of a situation here, my brother recently donated his old computer to my family and I installed Ubuntu 9.10 on it.
Things were great, but apparently my dad really wants to get to my brother's music. The thing is, I don't know how to get to it. I know his files are on the hard drive because I didn't format the drive, I just created a new partition and installed Ubuntu on it.
I can't explore the whole hard drive, just the partition I made. I've tried doing a search but it only comes up with files I've put on after Ubuntu.
So there are three questions I have for that.
1) How can I access the files?
2) Did I actually format it? :x
3)Would recovering Windows xp allow me to get to the files? If so, I've tried to recover by hitting f10 at boot and it just goes straight to Ubuntu.

Now I also cannot use a web browser. I have tried the pre-installed firefox and downloaded Galeon as well, neither start. I see it starting on the bottom of the screen, then it just disappears.
My other applications like Open Office work and open just fine.
What could have caused this / How do I fix it?

Sorry for any technical lingo butchering. :p
Thank you in advance.

---

### Post by taurus on 2009-12-27
If the windows partition is still there, then all you need is to mount it before you can access it.  Open a terminal and post the output of these commands, running one at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

And for firefox, run it from a terminal and see what kind of error message you would get.

```
firefox
```

---

### Post by Kempen on 2009-12-27
I put in the codes, and the only way I can help is with this picture.
[http://img12.imageshack.us/i/dscf7036d.jpg/](http://img12.imageshack.us/i/dscf7036d.jpg/)

For Firefox, it says bus error.

---

### Post by taurus on 2009-12-27
Try the first one again.

```
sudo fdisk -**[COLOR="Red"]l[/COLOR]**
```
That is a lower case letter L, not number 1.

---

### Post by Kempen on 2009-12-27
Ah that'd be the problem. Still... I'm not sure what to do from here?
[http://img30.imageshack.us/img30/8505/dscf7038.jpg](http://img30.imageshack.us/img30/8505/dscf7038.jpg)

Both Firefox and Galeon say bus error

---

### Post by taurus on 2009-12-27
Are you sure windows is still on it?  Did you tell the installer to use the whole drive when you installed it?  Is the harddrive 200GB?

---

### Post by Kempen on 2009-12-27
I'm not 100% sure if windows is still on it, I really don't believe I told the installer to use the whole disk, I just know I didn't format it. It's 200 GB.

---

### Post by taurus on 2009-12-27
You don't have to format the drive (or partition) first before you install Ubuntu.  The installer will format it for you once you tell it where to install to.  Looks to me like you nuked your windows in place of Ubuntu.

---

### Post by addist on 2009-12-27
Hi All,
I'm a newbie, My google earth picture doesnot good or not smooth, why? can somebody advice me, please?
I use Ubuntu 8.10, thx b4

---

### Post by Kempen on 2009-12-27
*facepalm* I guess I'll have to deal with my father's odd wrath over not being able to get to my brothers songs which I probably have anyway...
Thanks for your help on that end. I assume trying XP recovery wouldn't work if there's nothing to recover in the first place.

There is still the Firefox issue, any idea about that?

---

### Post by taurus on 2009-12-27
I am not sure this little app, [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk), can do any good now because the longer you use the machine, accessing the harddrive, the harder to recovery files from the previous installed.

---

### Post by taurus on 2009-12-27
> **addist said:**
> Hi All,
I'm a newbie, My google earth picture doesnot good or not smooth, why? can somebody advice me, please?
I use Ubuntu 8.10, thx b4

Why don't you create a new thread with your problem instead of hijacking another thread that's not even related.

---

### Post by Kempen on 2009-12-27
Thanks, but it has been over a month, maybe two by now since installing Ubuntu and honestly, it's not a big deal to get to the data.

I just would like to be able to browse the web on the computer because apparently my mom will be using it.

---

### Post by taurus on 2009-12-27
What's the spec of that machine?  How much RAM does it have?

```
free -m
```

---

### Post by infinitejones on 2009-12-27
Let's have a look at the firefox issue... open up a terminal, type firefox, and copy-and-paste the output into your reply.

(You can copy text from the terminal by highlighting it with the mouse, then holding down ctrl-shift-c. Then just paste as normal. Or you can click edit, copy from the menu along the top.)

---

### Post by Kempen on 2009-12-27
[http://img191.imageshack.us/img191/3558/dscf7039.jpg](http://img191.imageshack.us/img191/3558/dscf7039.jpg)
put in free -m ^^
As for specs, I really feel techno-tarded, but I have no idea.
It has 1GB of RAM.

Infinite, I would copy and paste...but I can't get to the internet on that computer. i'm working off of two separate computers right now. After I type firefox ALL it says it Bus error

---

### Post by infinitejones on 2009-12-27
I always find that Googling an error message works wonders when it comes to shedding light on things like this... I googled [ubuntu "bus error"]("http://www.google.com.au/search?q=ubuntu+"Bus+error"") and the very first link is this one:

[Bus error when running Firefox or Epiphany]("https://bugs.launchpad.net/ubuntu/+bug/133786")

It's a couple of years old, and there's a load of technical stuff on the page that you don't really need to worry about, but the most obvious thing to try is what's in the reply that xtknight wrote on 2007-08-26 (#3). Basically he just completely removed firefox and reinstalled it by typing these two commands into the terminal:

```
sudo dpkg --purge --force-all firefox
sudo apt-get install firefox
```
Give that a go and let us know how you get on.

---

### Post by Kempen on 2009-12-27
I actually did Google it and came to the same webpage, I'm tempted to drop the issue now because I downloaded Sea Monkey browser and it works fine now.
I put in the code and it asks me for my password, which I know is right because it's the one I use to log in, but it won't accept.
Could it be asking for a different password?

---

### Post by infinitejones on 2009-12-27
Shouldn't be - on Ubuntu, the password for sudo is the one you specified when you installed it and the one you use to log in.

Are you sure you don't have caps lock on without realising?

---

### Post by Kempen on 2009-12-27
Positive.
It asks for password, I try to type but no letters appear, so I have to hit enter, then it lets me type.

---

### Post by taurus on 2009-12-27
That is normal when you type in your password from a terminal.  There is no echo, not even ******.  So, make sure you enter the right password and when you are done, just hit the Enter.

Otherwise, make sure you belong to group adm if you want root privilege.

```
id
```

---

