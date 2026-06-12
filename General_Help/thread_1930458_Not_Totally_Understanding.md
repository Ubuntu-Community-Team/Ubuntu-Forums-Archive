---
title: "Not Totally Understanding"
date: 2012-02-23
forum: General Help
---

### Post by dritz33 on 2012-02-23
I have installed Ubuntu onto my laptop. I've been tinkering with it for a couple of weeks now. I can honestly say I have no idea how to use any of this stuff. I'm totally lost with installing programs and all of that stuff. Without Google I would have no programs installed on my laptop right now, because I can't figure out this system on my own.

Are there any really in-depth guides at learning how to use Ubuntu and/or the Linux OS in general?


Off-topic, I'm trying to learn how to create my own android app. This has been pretty hard seeing as how I have trouble even installing programs. Are there any android developers here who could break it down and explain it to a newbie?

---

### Post by HeroOfCanton on 2012-02-23
I switched all of my android development to linux (xubuntu) with very little pain fairly recently.

First, you will need to be using Eclipse. In the terminal (CTRL-ALT-T) type the following:

```
sudo apt-get install eclipse
```Then go here [http://developer.android.com/sdk/index.html](http://developer.android.com/sdk/index.html)

Download and unpack the SDK. I used my home directory as the SDK location.

Follow the instructions for installing the ADT from that site. Really not much to it.

I would make one suggestion, which is switch to KDE or XFCE for your desktop environment. Unity is not (IMO) useful for development. I gave it a two week shot and remained frustrated through the entire process. After switching to XFCE my development speed matches, or tops, what I could accomplish with Windows.

For general linux info I found this document to be pretty helpful [http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/10.10/en_US/screen/Getting%20Started%20with%20Ubuntu%2010.10.pdf]("http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/10.10/en_US/screen/Getting%20Started%20with%20Ubuntu%2010.10.pdf")

And, of course, the forums here. Lots of great people willing to help out.

---

### Post by dritz33 on 2012-02-23
> **HeroOfCanton said:**
> I switched all of my android development to linux (xubuntu) with very little pain fairly recently.

First, you will need to be using Eclipse.

```
sudo apt-get install eclipse
```Then go here [http://developer.android.com/sdk/index.html](http://developer.android.com/sdk/index.html)

Download and unpack the SDK. I used my home directory as the SDK location.

Follow the instructions for installing the ADT from that site. Really not much to it.

I would make one suggestion, which is switch to KDE or XFCE for your desktop environment. Unity is not (IMO) useful for development. I gave it a two week shot and remained frustrated through the entire process. After switching to XFCE my development speed matches, or tops, what I could accomplish with Windows.

For general linux info I found this document to be pretty helpful [http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/10.10/en_US/screen/Getting%20Started%20with%20Ubuntu%2010.10.pdf](http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/10.10/en_US/screen/Getting%20Started%20with%20Ubuntu%2010.10.pdf)

And, of course, the forums here. Lots of great people willing to help out.

I do have Eclipse downloaded and running fine, and I've downloaded the SDK (installing the 2.0-2.3 packages now) and I've got ADT plug-in installed on my eclipse. I'm not sure what an XFCE or an XDE is, so an explanation on that would be great :) 

I had a problem trying to get an AVD running, when I tried to create one it gave me an error saying it couldn't find a certain file I believe. I'm not sure what the exact error was, but after I install the rest of these packages I'll try to make an AVD again and see if the error persists.

---

### Post by MG&amp;TL on 2012-02-23
> **dritz33 said:**
> 

Are there any really in-depth guides at learning how to use Ubuntu and/or the Linux OS in general?


...there's several layers of abstraction. Depends whether you want to hack kernels or use LibreOffice. :) Assuming the latter, the built-in Ubuntu help is good, and google is the way to go. While it's perfectly possible to use an entire GUI system with Linux, it's still essentially a command-line OS, and if you want "in-depth", you would do very well learning the command line. 

It depends where you want to start.

Although I must say, I'm surprised you couldn't work out the software center...that has to be the easiest way of installing programs on the block.

---

### Post by HeroOfCanton on 2012-02-23
Think I know the error you're getting. When you are inputting the URL to install the SDK from click on the "Available Software Sites" link just below that box. Check the box that says "Helios Repository" or something like that.

Edit: I see that's a different problem. Post the error and I'll help if possible.

XFCE and KDE are desktop environments (DE). Basically an entirely different GUI. They feel more like windows and have great features like a start bar. Something I've not been without since Windows 3.1!

If you want to test them out you can just run:
```
sudo apt-get install xfce-shell
```and
```
sudo apt-get install kde-shell
```Then on the ubuntu login screen you will have the option to load to Unity, or one of the other DEs by clicking the arrow next to the username.

If you like one of the others, I would suggest a reinstall using the correct distribution (Xubuntu or Kubuntu). That's the great thing about linux. Choices!!!

---

### Post by dritz33 on 2012-02-23
> **HeroOfCanton said:**
> Think I know the error you're getting. When you are inputting the URL to install the SDK from click on the "Available Software Sites" link just below that box. Check the box that says "Helios Repository" or something like that.

Edit: I see that's a different problem. Post the error and I'll help if possible.

XFCE and KDE are desktop environments (DE). Basically an entirely different GUI. They feel more like windows and have great features like a start bar. Something I've not been without since Windows 3.1!

If you want to test them out you can just run:
```
sudo apt-get install xfce-shell
```and
```
sudo apt-get install kde-shell
```Then on the ubuntu login screen you will have the option to load to Unity, or one of the other DEs by clicking the arrow next to the username.

If you like one of the others, I would suggest a reinstall using the correct distribution (Xubuntu or Kubuntu). That's the great thing about linux. Choices!!!

When I try to run the command to get XFCE in terminal...this happens
```

[james@james ~]$ sudo apt-get install xfce-shell
sudo: apt-get: command not found
[james@james ~]$ ^C
[james@james ~]$ 

```


> **MG&TL said:**
> ...there's several layers of abstraction.  Depends whether you want to hack kernels or use LibreOffice. :smile:  Assuming the latter, the built-in Ubuntu help is good, and google is  the way to go. While it's perfectly possible to use an entire GUI system  with Linux, it's still essentially a command-line OS, and if you want  "in-depth", you would do very well learning the command line. 

It depends where you want to start.

Although I must say, I'm surprised you couldn't work out the software  center...that has to be the easiest way of installing programs on the  block.

What exactly is the software center?I'm not seeing that anywhere on my computer.

---

### Post by HeroOfCanton on 2012-02-23
Oops. Sorry it's

```
sudo apt-get install xubuntu-desktop
```

---

### Post by HeroOfCanton on 2012-02-23
Software center should be on the left menu button bar thingy (technical term :D) in unity.

---

### Post by dritz33 on 2012-02-23
> **HeroOfCanton said:**
> Oops. Sorry it's

```
sudo apt-get install xubuntu-desktop
```

Actually, fixed the apt-get problem. Now I've got that it can't find the xubuntu-desktop.

---

### Post by HeroOfCanton on 2012-02-23
Odd. Did you find the software center? You can search for xubuntu-desktop and install it from there too.

---

### Post by dritz33 on 2012-02-23
> **HeroOfCanton said:**
> Odd. Did you find the software center? You can search for xubuntu-desktop and install it from there too.

Yes I did. But, a search for both xubuntu-desktop and xubuntu returns no results.

Is there a way I can just install the whole xubuntu ontop of ubuntu without losing eclipse and everything I've spent a few hours downloading?

Could I possibly get your aim or any IM'ing service that you use? Would make this a little easier...if you do use one.

---

### Post by HeroOfCanton on 2012-02-23
Xubuntu can be found here [http://xubuntu.org/](http://xubuntu.org/)

The only way I know to do it without reinstalling everything is to do the apt-get or software center shell update. Try searching for XFCE maybe?

I haven't actually setup any IM on this computer yet, but I do need to. I'll send you a private message once I get it going.

---

### Post by dritz33 on 2012-02-23
> **HeroOfCanton said:**
> Xubuntu can be found here [http://xubuntu.org/](http://xubuntu.org/)

The only way I know to do it without reinstalling everything is to do the apt-get or software center shell update. Try searching for XFCE maybe?

I haven't actually setup any IM on this computer yet, but I do need to. I'll send you a private message once I get it going.

Alright, I'll be waiting for the IM :) And I might just give it up and uninstall ubuntu and grab xubuntu... My only problem with that is that the SDKs I downloaded took about 2 hours on their own, and that's kind of annoying.

---

### Post by evilsoup on 2012-02-23
I hope this isn't too late, but... [here](http://www.psychocats.net/ubuntu/xfce) are step-by-step instructions on how to install xubuntu/XFCE on top of regular Ubuntu. With pictures! And you won't lose anything you've installed already.

The reason you didn't find xubuntu-desktop when you searched for it was because it is considered a 'technical item' and so hidden by default in the Software Centre.

---

### Post by HeroOfCanton on 2012-02-23
> **evilsoup said:**
> I hope this isn't too late, but... [here]("http://www.psychocats.net/ubuntu/xfce") are step-by-step instructions on how to install xubuntu/XFCE on top of regular Ubuntu. With pictures! And you won't lose anything you've installed already.

The reason you didn't find xubuntu-desktop when you searched for it was because it is considered a 'technical item' and so hidden by default in the Software Centre.

He installed xubuntu and seems to be going good so far. Thanks though! I'm bookmarking that one. Normally apt-get works so I didn't know about that trick.

---

### Post by dritz33 on 2012-02-23
> **evilsoup said:**
> I hope this isn't too late, but... [here](http://www.psychocats.net/ubuntu/xfce) are step-by-step instructions on how to install xubuntu/XFCE on top of regular Ubuntu. With pictures! And you won't lose anything you've installed already.

The reason you didn't find xubuntu-desktop when you searched for it was because it is considered a 'technical item' and so hidden by default in the Software Centre.

Thanks for that, but I just decided screw it and redid my whole system with Xubuntu. Thanks though :)

---

