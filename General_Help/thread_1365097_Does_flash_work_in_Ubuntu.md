---
title: "Does flash work in Ubuntu?"
date: 2009-12-26
forum: General Help
---

### Post by greengiant83 on 2009-12-26
Does flash fully work in ubuntu and if so how can I make it work for me?  I am running ubuntu 9.10 64bit on my laptop.  When I visit site using flash in firefox all i see is a black box where it should be.  In google chrome it doesn't render at all.  

I have a desktop with ubuntu 9.10 64bit on it as well.  On this computer flash works...... almost.  YouTube and such video sites work, but some things with buttons in them don't react when clicked.  For instance pandora.com, and academicearth.org.  

What can I do to get flash into a usable state?

---

### Post by gsmanners on 2009-12-26
I'm using 64-bit Xubuntu 9.10, and I just tried Pandora. It worked just fine. I'm using the flashplugin-nonfree package.

---

### Post by jonest1 on 2009-12-26
There is a ppa for the latest 64-bit flash player/plugin from Adobe.  Run the following command in karmic to add the repository.

sudo apt-add-repository ppa:sevenmachines/flash

Follow that with 'sudo apt-get update'.  I believe the package is flashplugin64-nonfree.  So, if you have an older version installed, running 'sudo apt-get upgrade' should do the trick.  If not, run 'sudo apt-get install flashplugin64-nonfree'.

The current version in this repository is 10.0.42.34-0.

[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

---

### Post by jonest1 on 2009-12-26
One note, I got the command to add a repository wrong.  It should be the following:

sudo add-apt-repository ppa:sevenmachines/flash

Thanks spiderbatdad for pointing out the error.

---

### Post by greengiant83 on 2009-12-27
Thank you for the replies.  I tried installing the 64 bit version but it gives me the error:

E: Couldn't find package flashplugin64-nonfree

the previous commands for adding and updating the repository appeared to run fine with no errors.

So i installed flashplugin-nonfree.  On my laptop has youtube working a little bit, the video plays for a few seconds then freezes while the audio continues.  Academic earth's videos come up but are all yellow and the buttons inside seem to be cycling thru their various states.  Pandora gives me a nice cryptic error message: "We're sorry, but unless you agree to share registration information with %s, you will be unable to list to %s"  this error message is presented inside the flash applet, so its kind of working.

Any ideas why the 64 bit version couldnt be found?

---

### Post by gsmanners on 2009-12-27
Adobe doesn't make a 64-bit version of Flash (not just yet, anyway). What happens when you install flashplugin-nonfree is it downloads the normal 32-bit plugin from Adobe and then uses nspluginwrapper to link the plugin with the browser. Any time I have problems with Flash, I just quit out of Firefox and then reload Firefox to that page again and it works fine. Beyond that, I guess some video drivers might have problems. I don't really know, though.

---

### Post by greengiant83 on 2009-12-27
Is it possible that my problems with flash are solely because I am using the 64 bit version of ubuntu?  If I installed the 32 bit version of ubuntu, would flash work properly?

---

### Post by trubble on 2009-12-27
Flash 64 bit -- works great in Linux Mint 8.

Info > [http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

Download > [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

---

### Post by oldos2er on 2009-12-27
> **greengiant83 said:**
> Is it possible that my problems with flash are solely because I am using the 64 bit version of ubuntu?  If I installed the 32 bit version of ubuntu, would flash work properly?

64-bit flash works very well for me. Adobe released a refresh of it a few weeks ago.

---

### Post by blueridgedog on 2009-12-27
For 64 bit versions only, I have updated Romeo-Adrian Cioaba's scipt to download and install the latest version as released from adobe on 12/8 - version 10.0.42.34.

To run the script, open a terminal then 
```

cd ~/Downloads
sudo chmod 700 native-64bit-flash-installer2.sh
sudo ./native-64bit-flash-installer2
```

This assumes you download the file into your Downloads directory.

The script itself contains the following commands, credit to Romeo-Adrian Cioaba for the script:

```
echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
```

---

### Post by dcstar on 2009-12-27
> **oldos2er said:**
> 64-bit flash works very well for me. Adobe released a refresh of it a few weeks ago.

+1

---

### Post by sigurnjak on 2009-12-27
Did any of you try playing Yoville on Facebook ? It is kind of important to my wife !:)

---

### Post by greengiant83 on 2010-01-02
Thank you, that works wonderfully.

---

