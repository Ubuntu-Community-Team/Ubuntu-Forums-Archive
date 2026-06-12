---
title: "Linux Experts, I need your help. (:"
date: 2009-08-25
forum: General Help
---

### Post by madarieder on 2009-08-25
I want to dual boot XP and UNR on my Asus Eee pc 1005ha. I have both already installed, but I need to get the wireless working. I found this [http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/) tutorial. Its way too confusing though. 

I'm stuck here: 
> Wired networking
After install, the first thing you&#8217;ll notice is that ethernet and wireless networking aren&#8217;t working. Fortunately, they&#8217;re easy to fix.
On a computer with working networking, download this file:
atheros-wired-driver-1005ha-linux
Open the zip file (double-click it), and extract it to the location of your choice. Then, in a terminal, navigate (&#8217;cd&#8217;) to the &#8217;src&#8217; directory of the unpacked files, and type:

make
sudo make install
sudo insmod atl1e.ko
If you receive an error after the first line, and you&#8217;re not running Ubuntu Jaunty UNR, ensure you have the linux headers package installed for your kernel &#8212; you&#8217;ll need to find and download the appropriate .deb and install it. Information is here.
Until Ubuntu Karmic is released, every time you do a kernel update, you will need to re-run the last two steps (preceded by a sudo rmmod atl1e.ko).
You now have ethernet network &#8212; so plug yourself in to a network cable and set up wireless&#8230;

This is my first time using linux, so.. meh. I'm totally lost. Thanks in advance guys. I really appreciate it.

---

### Post by bodhi.zazen on 2009-08-25
What version of Ubuntu ?

In general Ubuntu 9.04 has much better hardware detection , including wireless, then earlier versions.

I suggest your try Xubuntu 9.04

---

### Post by 3rdalbum on 2009-08-25
> **bodhi.zazen said:**
> What version of Ubuntu ?

In general Ubuntu 9.04 has much better hardware detection , including wireless, then earlier versions.

I suggest your try Xubuntu 9.04

The HOWTO is for Ubuntu Jaunty (take a look at the link) and you probably won't get much benefit from running Xubuntu instead of Ubuntu.

I started writing a detailed post for you, before realising that you don't have Ethernet drivers. Frankly, this is going to be a major pain in the backside for you to get running (how on earth did Asus manage to find a wireless card AND an Ethernet card that AREN'T supported on Ubuntu 9.04??). I'd recommend downloading the latest alpha version of Ubuntu 9.10, because it's more likely to have the necessary drivers built-in.

This is why it's important to check on Linux compatibility before buying any piece of computer hardware.

If you absolutely must get 9.04 running, then you'll need to go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and do searches for these packages:

1. build-essential (and all the packages listed under "depends" on the page where you download the build-essential package)
2. The "linux-headers-generic" package corresponding to the version of the kernel that your computer is running (you can find out your kernel version by typing "uname -r" into the terminal. You can find the terminal under Applications > Accessories).
3. nautilus-open-terminal

Obviously, as you have no Ethernet, you need to use another computer to download these files. Additionally, you need to download the file that the instructions tell you to (which is the actual driver).

Transfer the packages and the driver to the Eee using a USB drive. Specifically, you should put these files DIRECTLY into your home directory for the time being. Open the terminal again by going Applications > Accessories > Terminal, and type the following:

```
sudo dpkg -i *.deb
```

This installs all the Ubuntu packages you downloaded. If it complains that you're missing a package ('dependency problems') then download the requested package from the website and put it in your home directory, and then try again.

Once you are done, you should have the necessary tools to actually build the driver from its source code. You can delete all the files ending in ".deb" from your home directory now, but don't delete the actual driver archive. If you haven't done so already, log out and log in again to make sure that the "nautilus-open-terminal" plugin becomes active.

Double-click the driver archive, it will open in the archive manager program. Extract it somewhere you can get at it easily (your Desktop folder, or a new folder, or somewhere). Click the "Open Destination" button, or otherwise go to the folder where the driver was extracted to.

When you're looking at the contents of the folder (it should contain a number of files, I believe), right-click in some empty space and choose "Open Terminal Here". Another terminal window will open.

Now you can type the following commands (that the instructions gave you):

```

make
sudo make install
sudo insmod atl1e.ko

```

The last bit of the last line is an A, a T, an ell, a number one etc.

You now have Ethernet, and I assume there are instructions on that web page for setting up the wireless part. Now that you have kernel headers and the "build-essential" environment, it gets easier from here.

Note that you will need to run those last three commands every time you download a kernel update.

Yes, as I mentioned this is a pain in the rear, so please try Ubuntu 9.10 first. I don't know if there's a "netbook remix" version of it yet, so just use ordinary Ubuntu 9.10 - it works just as well. Hopefully everything will Just Work out-of-the-box and you won't need to compile drivers.

I'm subscribing to this thread so if you have any problems, post a reply to this thread and I should see it.

Oh and next time, please research Linux compatibility before buying computer hardware :-)  Good luck.

---

### Post by bodhi.zazen on 2009-08-25
Ah thanks. 

And just to throw out a few alternates, you can look at moblin

[http://moblin.org/](http://moblin.org/)

Or Fedora 11.

If one of those options recognizes your hardware it will be easier.

If you want to stay with Ubuntu, can you connect to a wired network until you have your wireless working ?

---

### Post by 3rdalbum on 2009-08-26
> **bodhi.zazen said:**
> If you want to stay with Ubuntu, can you connect to a wired network until you have your wireless working ?

Yeah, but he/she needs to follow the instructions I gave to get the Ethernet working. That's why it's such a pain - I had almost finished writing a set of instructions using Synaptic to get all the packages, and then I saw this part of the post:

> Wired networking
After install, the first thing you&#8217;ll notice is that ethernet and wireless networking aren&#8217;t working.

So I had to modify it all to say how to download packages from a different computer.

---

### Post by zkriesse on 2009-08-26
Wireless is actually quite easy to set up. Opposite click on system go to edit menus. Go down to preferences then make sure that the option network connections is clicked. Close the menu. Then go to System/Preferences/Network Connections. Go to the Wireless tab. It should show the available networks that you can connect to. Click the one that you want and then click the Edit tab to the right of the screen. Make sure that the Connect Automatically option is checked if you want it to connect when the wireless is turned on. Hopes this helped.

---

### Post by P4man on 2009-08-26
wow.. im shocked too. A modern netbook, and neither wired nor wireless are working out of the box?!

**madarieder**, if you want to use ubuntu, you're gonna have to prepare for spending more time and effort than.. well, needed.. really. You won't be dipping your toes in linux, you will be diving in head first lol. 

I can only suggest you borrow, buy or steal ;) an USB wifi stick that **is **supported out of the box (95% of them are). That way at least you can test ubuntu a bit,  download stuff, visit this forum while trying to solve the rest.

But I won't lie. if this is your first linux experience, you may well be put off by it. Big time. And I couldnt blame you for it. I would seriously consider looking for alternatives to ubuntu that better support your hardware. Once you get the hang of linux, you can always revisit ubuntu and try to make things work, or perhaps by then a new release will support your machine without jumping through loops.

If you wanna give this a try nonetheless, let us know if you can get a hold of a wifi stick or not, and then we can try and talk you through it.

---

### Post by madarieder on 2009-08-26
> **P4man said:**
> wow.. im shocked too. A modern netbook, and neither wired nor wireless are working out of the box?!

**madarieder**, if you want to use ubuntu, you're gonna have to prepare for spending more time and effort than.. well, needed.. really. You won't be dipping your toes in linux, you will be diving in head first lol. 

I can only suggest you borrow, buy or steal ;) an USB wifi stick that **is **supported out of the box (95% of them are). That way at least you can test ubuntu a bit,  download stuff, visit this forum while trying to solve the rest.

But I won't lie. if this is your first linux experience, you may well be put off by it. Big time. And I couldnt blame you for it. I would seriously consider looking for alternatives to ubuntu that better support your hardware. Once you get the hang of linux, you can always revisit ubuntu and try to make things work, or perhaps by then a new release will support your machine without jumping through loops.

If you wanna give this a try nonetheless, let us know if you can get a hold of a wifi stick or not, and then we can try and talk you through it.
I decided to just download the Alpha. Everything works fine wireless wise .I have no idea how to install anything. I was reading this [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) . I don't have that gdebi package installer on my computer. Help?

---

### Post by P4man on 2009-08-26
> **madarieder said:**
> I decided to just download the Alpha. Everything works fine wireless wise .I have no idea how to install anything. I was reading this [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) . I don't have that gdebi package installer on my computer. Help?

from that link "If you are using Ubuntu 9.04, this tutorial will be useless to you". That applies a fortiori to ubuntu 9.10 :)

Installing stuff in linux is quite different to windows. in windows world you wibble over web hunting for apps and drivers, then you download something executable that you double click to install, and you pray its compatible with your hard- and software, doesnt contain virusses or malware and will actually work.

In the ubuntu world, your PRIME source of apps and stuff is the repositories.  Glance over this:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

With those repositories, you can add (tested, trusted, compatible)  programs through applications > add/remove software. 

more programs and packages are available in the slightly less userfriendsly Synaptic package manager (system > adminstration > Synaptic).

Everything you can download and install that way, you can also install from the terminal (command prompt). That is easier for us to type, and probably faster to use if you someone typed it for you :). 

lets try the terminal approach. Go applications > accessoiries > terminal and type:

```
sudo apt-get install ubuntu-restricted-extras
```

That will install a package called restricted extra's, which contains flash plugin, java, a lot of music and video codecs (including MP3) and other stuff you will likely need.

If you only want flash player, you can do:

```
sudo apt-get install adobe-flashplugin
```

Of course, you can also use add/remove programs or the synaptic package manager :)

BTW, you can paste a command in the terminal useing shift+control+V
So you can copy it from the forum, paste it in a terminal, hit enter, type your password, and thats pretty much all.

---

### Post by madarieder on 2009-08-26
I went through the synaptic method. I restarted the browser and it works. :) thanks so much.

---

### Post by P4man on 2009-08-26
Did you install ubuntu yet, or are you still on a live CD ?

BTW, you are probably aware 9.10 is still in alpha. I havent tried alpha 4 yet, but alpha 3.. well.. lets just say it wasn't quite ready for prime time yet. or it didn't like me :p Hope you are luckier :)

One more thing. If you are looking for documentatin or help.. start here:

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

(use the search if appropriate).

If you search on google, add "jaunty" or "karmic" to the search terms, so you dont get outdated howto's. Things have changed quite a bit over the years. But most things that apply to jaunty (9.04) should work in karmic (9.10).

---

### Post by madarieder on 2009-08-26
> **P4man said:**
> Did you install ubuntu yet, or are you still on a live CD ?

BTW, you are probably aware 9.10 is still in alpha. I havent tried alpha 4 yet, but alpha 3.. well.. lets just say it wasn't quite ready for prime time yet. or it didn't like me :p Hope you are luckier :)

One more thing. If you are looking for documentatin or help.. start here:

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

(use the search if appropriate).

If you search on google, add "jaunty" or "karmic" to the search terms, so you dont get outdated howto's. Things have changed quite a bit over the years. But most things that apply to jaunty (9.04) should work in karmic (9.10).

I downloaded it. I actually deleted the 9.04 partition, and replaced it with 9.10. 

I also want to download this : [http://kmess.org/download/](http://kmess.org/download/) . I don't know how to though. is it the same process?

---

### Post by P4man on 2009-08-26
yep. its in the repo's.

Add/remove programs (make sure you show "all available applications" then search for kmes. Its there.

HOWEVER.

ITs a KDE app. Its meant to integrated in the KDE desktop environment, and I assume you are using GNOME (kubuntu = with KDE while ubuntu = with gnome). You can run KDE apps on GNOME, but it will be a big download as you will need to install the KDE core, and it not look so nice on GNOME. If you want an MSN messenger for gnome, try pidgin, emesene, aMSN, ...

If you want to try out KDE:

```
sudo apt-get install kubuntu-desktop
```

Log out, and in session select "KDE" and see if you like it.

---

### Post by madarieder on 2009-08-26
Okay. I'm having an idiot moment here, but where's the add/remove programs?

---

### Post by P4man on 2009-08-26
in the applications menu :) Bottom of it ..
edit: you are using Ubuntu and not Kubuntu are you ?

---

### Post by madarieder on 2009-08-26
> **P4man said:**
> in the applications menu :) Bottom of it ..
edit: you are using Ubuntu and not Kubuntu are you ?
I'm using ubuntu. the netbook remix.

---

### Post by P4man on 2009-08-26
Ah! LOL
Well, then I dont know ROFL. Never used the netbook remix shell. Perhaps somewhere under settings? No clue where they hid it. Command line will work though :p

```
sudo apt-get install kmess 
```

(but again, im not sure its a good idea to install a KDE app at this point. It will warn you though about needing to install a ton of stuff.

---

### Post by madarieder on 2009-08-26
> **P4man said:**
> Ah! LOL
Well, then I dont know ROFL. Never used the netbook remix shell. Perhaps somewhere under settings? No clue where they hid it. Command line will work though :p

```
sudo apt-get install kmess 
```(but again, im not sure its a good idea to install a KDE app at this point. It will warn you though about needing to install a ton of stuff.

I figured it out. xD I ended up using the add/remove thing. I installed amsn.

---

### Post by P4man on 2009-08-26
perhaps that ubuntu logo top left, does that provide access to the "normal" menu's ?

---

### Post by madarieder on 2009-08-26
Turns out you can switch to desktop mode. Everything is a lot less confusing :P

---

### Post by P4man on 2009-08-26
eeh.. I hope they fixed a nasty bug in that desktop mode switcher :S
Seen a ton of people breaking their gnome after using it.

---

### Post by madarieder on 2009-08-26
So far everything has been fine. So, I'm guessing its fixed/ :)

---

