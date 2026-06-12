---
title: "Beginner question."
date: 2011-04-02
forum: General Help
---

### Post by muhammadalidildar on 2011-04-02
I've switched from Microsoft's windows to Ubuntu after 7 years. I am totally unfamiliar with ubuntu's environment.

(i) I've downloaded a software but don't know how to compile and run it. I didn't download it from "Ubuntu Software Centre", rather I used firefox built-in downloader.
Please guide me a little so that I am able to install/compile and run programs.

(ii) Secondly, as I am using Ubuntu desktop edition 10.10 so I am facing some problems like sometimes Software Centre do not run properly and closes after a blink and same with some other programs and I've to restart my PC. Does Ubuntu 10.10 contains some bugs?

Thanks.

---

### Post by Shibblet on 2011-04-02
> **muhammadalidildar said:**
> I've switched from Microsoft's windows to Ubuntu after 7 years. I am totally unfamiliar with ubuntu's environment.

Hello!  Welcome to the forums.

> **muhammadalidildar said:**
> (i) I've downloaded a software but don't know how to compile and run it. I didn't download it from "Ubuntu Software Centre", rather I used firefox built-in downloader.
Please guide me a little so that I am able to install/compile and run programs.
Since you are first starting off, I will give you the best advice for a newbie that I can.  Ubuntu is different from Windows.  You will not be scouring the web trying to find an installer package to compile and run.  

Just use the software center for now, until you are comfortable with installing from source.  Installing from source can be tricky.  But the software center works great!

> **muhammadalidildar said:**
> (ii) Secondly, as I am using Ubuntu desktop edition 10.10 so I am facing some problems like sometimes Software Centre do not run properly and closes after a blink and same with some other programs and I've to restart my PC. Does Ubuntu 10.10 contains some bugs?

When I first installed Ubuntu 10.10.  My first task was to run the update manager.  That usually downloads the new kernel, and that is one of the only things that requires your computer to restart.  So, restart with the new kernel, and then you should be running fine.  

I have an Nvidia graphics card, so I run System > Administration > Additional Drivers, and then allow Ubuntu to update my graphics card drivers.  This usually requires a reboot as well.

Other than that.  I will give you fair warning.  You have to break your mind of how Windows works.  Ubuntu (Linux in general) is not Windows.  It will not work the same way as Windows.  It is not a Windows replacement, or a free version of Windows.

Ubuntu is it's own Operating System.  That means things work great, but things work different from Windows.  If this is a bit too much to begin with, I suggest running a Wubi install until you are more comfortable.

I personally dual-boot my machine, because I have work that needs to be done in Windows.  And unfortunately Ubuntu will not run all of my programs, even with Wine.  I also play some games from time to time, and they run in Windows.

Any of my personal stuff, I do in Ubuntu.

---

### Post by muhammadalidildar on 2011-04-02
Thank you very much for your kind support.

Actually I am already in computer science field and generally I can differ windows and linux. I am beginner in ubuntu but not in computer field. So I can grasp the new concepts as I've learned (still learning) computer languages and lot more. I know the concept of source compilation etc...

So I want to learn linux from A-Z.

Waiting for your response...

Thanks.

---

### Post by lisati on 2011-04-02
I, too, sometimes find it easier to use the Software Center instead of other metthods, even though I've been using Ubuntu for nearly four years and computers of one form or another for something like 30 years....

Installing software can depend on the way it is packaged.

If it's a ".deb" file, one option is to open the file from the Desktop. With "standard" Ubuntu, this will open up a dialog with a button that will let you install the software. From the command line, one equivalent to this process is with something like the following:
```
sudo dpkg -i {path-to-deb-file}
```

---

### Post by oldsoundguy on 2011-04-02
The hardest thing when switching from Windows to Linux is to get your head around the idea that Linux IS NOT Widows and what works in one, most of the time will NOT work in the other.

Another thing is that Linux does things the easy way.  They are not trying to impress some computer science professor with their bells and whistles.  The Software Center and Synaptic should take care of almost everything you need to get up and running with alternative programs to the paid stuff in Windows.
Gone are the days when you had to use terminal all the time and .tar/gz anything  to get it installed and working in your system.  I think I had to use Terminal all of once last month.  And that was to re-set my configuration on my cable connection.

To ME, Linux is a background program that just stays there and allows me to run other things and to accomplish tasks without sticking its fingers into everything just to let you know it is there.
I hardly ever see my desktop as all of the programs I use most of the time are quick launch in the Gnome panel.  And the pull down menus for the the stuff I use .. but not as often.

As to bugs .. most I have noticed from posts here  occur on laptops, not desktops. (proprietary nature of the laptops)

---

### Post by bk60544 on 2011-04-02
Hi and Welcome to Ubuntu.
>>I am also running U-10.10 [dual-booting with Win7] and have had no problems with either the Software Center or Update Manage
>>I've been in both the Mac and Windows world for more than 20 years, so a different platform and OS can be challenging.
>>My biggest issue is the difference in terminology.  As my daughter would say, "I don't want to LEARN it, I want to KNOW it."
Hope you have an easier transition than I've had; and the Forum is a GREAT place to get info, tips and advise.

---

### Post by Dave_L on 2011-04-02
muhammadalidildar:

(i) Could you provide some more details about the software you downloaded?

(ii) I'm using Ubuntu 10.04 rather than 10.10, and I generally use synaptic rather the the Software Center. I rarely have problems installing or upgrading packages.

---

### Post by Anonymous is Incognito on 2011-04-02
First of all, welcome.

In addition to everything that has been said already, I'd like to add some other things.

*In Linux, one task can be completed in a several hundred ways.* Each of these has it's pros and cons. It is generally up to you which method you pick. To illustrate this I would like to add the example of installing new software - packages - You can do this via the software center - a GUI method - or using the command line - typing - Once you get the hang of it, the typing method is faster, but the GUI method has less of a learning curve.

[This guide]("http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html") details how you can use [FONT="Courier New"]apt-get[/FONT] - the typing/terminal based method - to install packages from the repositories. It also has a little section on how to use [FONT="Courier New"]dpkg[/FONT] to install the [FONT="Courier New"].deb[/FONT] file that any Debian based distro uses to install applications.

On another note, let's talk about man pages. These are the documentation that comes with the applications you install. See it like a manual for the particular application. The below code will give me the manual for apt-get. - press [FONT="Courier New"]q[/FONT] to quit -

```
man apt-get
```

I think this will solve quite a few of your first troubles. Feel free to post another general question in this thread, or, if your problem is a bit more specific, it is better to create a new thread in the appropriate support category.

---

### Post by treehermit on 2011-04-02
Hi Muhammad,

There's one more thing you can do:

Install the 'GDebi Package Installer' and the 'Aptitude Package Installer' from the Software Center. This will help u compile/ Install some packages that you download from the source.

Best of Luck

---

### Post by muhammadalidildar on 2011-04-03
Thanks a lot for all your support.

Dave I've downloaded "winehq". First I tried to download it from Software Centre but that was very very time consuming that is why I chose the 2nd way.

---

### Post by Anonymous is Incognito on 2011-04-03
Glad to be of help.

Don't forget to mark the thread as solved if your problem is gone - it is under thread tools -

---

### Post by cjsteele on 2011-04-03
> **muhammadalidildar said:**
> I've switched from Microsoft's windows to Ubuntu after 7 years. I am totally unfamiliar with ubuntu's environment.

(i) I've downloaded a software but don't know how to compile and run it. I didn't download it from "Ubuntu Software Centre", rather I used firefox built-in downloader.
Please guide me a little so that I am able to install/compile and run programs.

(ii) Secondly, as I am using Ubuntu desktop edition 10.10 so I am facing some problems like sometimes Software Centre do not run properly and closes after a blink and same with some other programs and I've to restart my PC. Does Ubuntu 10.10 contains some bugs?

Thanks.

There are a million good tutorials (or more) on how to compile software under Linux (generally), and Ubuntu (specifically.)  The basic process though, is typically something along the lines of:

```

sudo apt-get install build-essentials
tar -zxvf <yourpackage>.tar.gz
cd <yourpackage>
./configure
make
make install

```

If that doesn't work, well... there's always google.

As for software center not working properly, that's a bit odd.  Ordinarily, it just runs... try running it from a terminal, you might get some helpful debug output.  Its called `/usr/bin/software-center`, so you should just be able to run that from a terminal, and it should provide you some information.


Cheers,
-C

---

### Post by muhammadalidildar on 2011-04-03
One more question I want to ask.
If I would be in windows, I'll write a command like this:
D:
cd DirectoryName

to traverse from one directory to another.

How can I traverse in ubuntu through 'terminal'?

---

### Post by newbuntuxx on 2011-04-03
useful ubuntu commands:

traverse directories:

```
cd directory_name
```

to go to home

```
cd ~
```

To go to root "/" (which is like C:)

```
cd /
```

to list files in a directory:

```
ls
```

to mv a file from my directory to another:

```
mv filename /path/to/dir
```

to copy a file in the same directory or to another directory:

```
cp filename1 filename2
```

to rename a file:

```
mv initialfilename secondfilename
```

To create a file:
```
touch filename
```

to edit a file:

```
nano filename
```

to delete a file:

```
rm filename
```

to create a directory:

```
mkdir directoryname
```

to delete a directory:

```
rm -rf dirctoryname
```

to output the contents of a file:

```
cat filename
```

to search for files starting from the root (/) (c:) and working your way day the directory structure:

```
sudo find / -iname "filename"
```

to search a file for specific string:

```
cat filename | grep "string_to_find"
```

to output a file "slowly"/with control:

```
more filename
```

to be able to scroll up and down through the outputted file:

```
less filename
```

---

### Post by Topsiho on 2011-04-03
If you stick to using the ubuntu repositories, you need not be afraid of installing malware together with the application you install from there. I know no better than that they can be trusted.

If you use ***trusted*** sources you also maybe may be not afraid for that ...

Viruses can not install themselves, if they don't know your password (and how could they?), and if you do not operate normally as root. So if you work as a normal user, without administration rights, you are safe in this respect.

Using the repositories the downside is that the packages may be some versions behind, so if you want the newest version, you must get it and compile it yourself.

For that, as someone already told you, you have to install build-essentials ONCE, and then most applications can be installed the way he told you. Or read the READ file that often is coming with the source, in which you may find instructions. You also have to take care of the dependencies (other programs and libraries it needs) yourself.

My two eurocents :)

Topsiho

---

