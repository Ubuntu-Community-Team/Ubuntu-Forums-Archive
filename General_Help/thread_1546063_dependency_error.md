---
title: "dependency error"
date: 2010-08-04
forum: General Help
---

### Post by mindlessbrain on 2010-08-04
Hi all, 

First of all the computer I have Ubuntu on does not have internet access. So every package I download I have to download in .deb form on another computer and then switch it over. Mostly this has been going fine, except for now.

I'm trying to get build_essential installed so I stop getting errors when I try to "make" a .tar file to install bwa, a bioinformatics aligning program. 

So I went and downloaded build-essential_11.4build1_i386.deb with all its dependencies. 

The big problem is when I try to install 
g++-4.4_4.4.3-4ubuntu5_1386.deb I get an error saying 

"Error: Dependency is not satisfiable: libstdc++6-4.4-dev (=4.4.3-4ubuntu5)"

The big problem here is that I went and download libstdc, and when I go to install it says its already installed. I've reinstalled it a few times and then restarted the computer, but no go. libstdc still says its installed, and g++-4 says its not. 

Help?

Thanks in advance!

---

### Post by dv3500ea on 2010-08-04
Try using [keryx]("http://keryxproject.org/").
It worked great for me before I got wireless.

---

### Post by oldos2er on 2010-08-04
Which version of Ubuntu are you running?

---

### Post by elliotn on 2010-08-05
Use synaptic then when it says the following programs will be installed copy them into a text file, that way u have all dependencies

---

### Post by EXCiD3 on 2010-08-05
[Keryx]("http://keryxproject.org") should be a big help in gathering dependencies for you. :)

If you need any help with it, just shoot me a message. I'm hard at work on the next version which is a HUGE improvement. :D

---

### Post by realzippy on 2010-08-05
> **mindlessbrain said:**
> Hi all, 

First of all the computer I have Ubuntu on does not have internet access. So every package I download I have to download in .deb form on another computer and then switch it over. Mostly this has been going fine, except for now.

I'm trying to get build_essential installed so I stop getting errors when I try to "make" a .tar file to install bwa, a bioinformatics aligning program. 

So I went and downloaded build-essential_11.4build1_i386.deb with all its dependencies. 

The big problem is when I try to install 
g++-4.4_4.4.3-4ubuntu5_1386.deb I get an error saying 

"Error: Dependency is not satisfiable: libstdc++6-4.4-dev (=4.4.3-4ubuntu5)"

The big problem here is that I went and download libstdc, and when I go to install it says its already installed. I've reinstalled it a few times and then restarted the computer, but no go. libstdc still says its installed, and g++-4 says its not. 

Help?

Thanks in advance!

Have you tried to force install?

```
sudo apt-get install -f
```

---

### Post by EXCiD3 on 2010-08-05
> **realzippy said:**
> Have you tried to force install?

```
sudo apt-get install -f
```

You missed the part that he's on a computer without internet access.

---

### Post by realzippy on 2010-08-05
OH.
So what about

```
sudo dpkg --install --force-all
```

or would apt-get complain afterwards?

---

### Post by EXCiD3 on 2010-08-05
> **realzippy said:**
> OH.
So what about

```
sudo dpkg --install --force-all
```

or would apt-get complain afterwards?

Yeah, but if you're missing dependencies, you'll get broken packages doing that. 

The easiest way to do it is using Keryx. You just create a snapshot of your offline machine, then use Keryx to get the dependencies for you. Since he can't download them on his own machine, pretty much all those tools are useless until he gets the packages some other route. It's a real pain in the butt but what we're working on with Keryx helps to solve that.

---

### Post by nothingspecial on 2010-08-05
OK

To use linux efficiently you need the internet.

It is possible to use it without but it is a hell of alot of messing about.

Download stuff you need from here

[http://packages.ubuntu.com/lucid/](http://packages.ubuntu.com/lucid/)

For each package you want to install, you have to download the dependencies, then check their dependencies and so on until you have exhausted the list.

Put them all into one directory, cd into that directory and type
```

sudo dpkg -i *.deb 
```and cross your fingers that dpkg will sort it out.

Or get an internet connection

---

### Post by EXCiD3 on 2010-08-05
> **nothingspecial said:**
> OK

To use linux efficiently you need the internet.

It is possible to use it without but it is a hell of alot of messing about.

Download stuff you need from here

[http://packages.ubuntu.com/lucid/](http://packages.ubuntu.com/lucid/)

For each package you want to install, you have to download the dependencies, then check their dependencies and so on until you have exhausted the list.

Put them all into one directory, cd into that directory and type
```

sudo dpkg -i *.deb 
```and cross your fingers that dpkg will sort it out.

Or get an internet connection

An internet connection is not always possible. And this is not  always a good idea:

```
sudo dpkg -i *.deb
```

This can cause packages to break, it used to be our old suggested installation method for [Keryx]("http://keryxproject.org") but a lot of users responded back that packages were broken afterwards. Sometimes --force is needed to install in this method as well and can cause havoc. Generally it works, but you'd be better off downloading the packages and the package list files and copying them to the apt cache on your offline machine and installing through apt-get. It will throw errors on apt-get update trying to contact the server, but it will read through the new lists and since the packages are already in the cache it won't attempt to access the internet to download packages. This is our new installation method for Keryx and it will never break a user's system.

---

### Post by nothingspecial on 2010-08-05
> **EXCiD3 said:**
> An internet connection is not always possible. And this is not  always a good idea:

```
sudo dpkg -i *.deb
```This can cause packages to break, it used to be our old suggested installation method for [Keryx]("http://keryxproject.org") but a lot of users responded back that packages were broken afterwards. Sometimes --force is needed to install in this method as well and can cause havoc. Generally it works, but you'd be better off downloading the packages and the package list files and copying them to the apt cache on your offline machine and installing through apt-get. It will throw errors on apt-get update trying to contact the server, but it will read through the new lists and since the packages are already in the cache it won't attempt to access the internet to download packages. This is our new installation method for Keryx and it will never break a user's system.

Ok

You are clearly part of a project to fix this issue.

I was just pointing out how you (used??) to do it.

Go with what this guy says

---

### Post by EXCiD3 on 2010-08-05
Hehe, yeah I have just spent a lot of time around this issue because I had dialup at home until 2 months ago. :P

Just trying to help clear some of the misconceptions that seem to be spreading around. Like that stupid synaptic download script...it only works if you can download the package lists on your machine. I see people recommending it because it's "official" since it's in Synaptic, but really, it doesn't do what most people need. Quite a confusing array of choices that you have, and some suggestions just plain don't make sense.

Oh well, that's how it goes sometimes. Hope I didn't step on anyone's feet! :P

---

### Post by mindlessbrain on 2010-08-06
I downloaded keryx and put it on both this computer with internet and the computer without internet. It runs fine on the computer without internet except that it wants to download stuff and that just isn't happening. 

Then when I have it on the computer with internet and running windows I get the startup window asking me if I want to start a new project or open an old one. I don't have any old projects, so I clicked start a new one. Then it keeps telling me to "Please create a project compatible with the plugin's supported OS". The only option I have is Debian. 

*sigh* I'm really starting to wonder if this will ever get fixed. I seriously need to install something to be able to install something? Seriously?

I also tried loading things directly from the disk I used to install. 

```

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v

```

Then I get an error saying "Failed to fetch CD" or something like that. I've reburned the CD a few times (10.04 LTS) and restarted the computer a few times to try it again, but it never works. Same thing if I insert the CD and try to fetch it using the Synaptic package manager.

Thanks everyone who wrote in! Hopefully I will have the internet soon and this won't be such a PITA.

P.S. I am a girl.

---

### Post by mindlessbrain on 2010-08-06
Sorry! I use it on the non internet computer first, and then transfer over. Dur.

---

### Post by mindlessbrain on 2010-08-06
Ok so I ran it on ubuntu, then over on my windows where it downloaded all the packages. So then I go back to linux, and go from the project menu go to install packages. 

Then I get an error saying 

"Failed to update the APT cache. Aborting installation."

WTH? I was really beginning to think this would actually work...

---

### Post by mindlessbrain on 2010-08-06
Ok. Used keryx and got the packages downloaded. Moved it to my other computer, copied it off the thumb drive and then restarted. This got rid of the ATP error.

THEN I got another error saying I had broken packages.

Eventually I figured out I was able to go into the project/packages folder and just click on the .deb for build-essential and install. I wish all the other packages had installed too, but that was what I needed. 

Now I'm trying to get bwa installed, a bioinformatics mapping tool. It says to use make, but doesn't explicitly say what I need to do and I could really use some tips!

---

### Post by nothingspecial on 2010-08-06
If you click into the folder (if you see what I mean), is there a MAKEFILE?

---

