---
title: "What The Hell Is Up With Java Runtime Environment?"
date: 2006-02-22
forum: General Help
---

### Post by Mark76 on 2006-02-22
It refuses to play nice.  I can't get it to work in Opera (my preferred browser) OR Firefox.

I'm really beginning to loathe the people who wrote the code for it :mad:

---

### Post by Mark76 on 2006-02-22
Must.  Remember. To. Subscribe. To.  Thread

---

### Post by nrwilk on 2006-02-22
You can set an option in your profile which automatically subcribes you to a thread whenever you post to it.

Also.  Whenever I reinstall, I use this howto to get my java running:

[http://ubuntuforums.org/showthread.php?t=76754](http://ubuntuforums.org/showthread.php?t=76754)

Just remember that whenever a command in this howto referrences the name of the jre file, replace it with the name of the file you downloaded.  Instead of jre-1_5_0_05-linux-i586.bin, it should be jre-1_5_0_0[COLOR="Red"]6[/COLOR]-linux-i586.bin.  Notice the digit in red is 6 instead of the 5 which appears throughout that howto.

Also, when the howto tells you to "chose the sun java option," remember that in the options you will have, none will have the actual word "sun" in them.  But, the option you want will be the third one.

A good tip is that the terminal will complete things for you, if you hit the tab key.  So, instead of typing out that whole file name, just type "jre" and hit tab, and it will fill in the rest for you.  you have to be in the directory where the file is for this to work, or have typed it's location before it ( like this: /home/<yourusername>/Desktop/jre ).

---

### Post by Mark76 on 2006-02-22
How do I do this?

 Create a symlink from /usr/lib/mozilla/plugins/libflashplayer.so to /usr/lib/opera/plugins/libflashplayer.so

---

### Post by 5-HT on 2006-02-22
[QUOTE=Mark76]How do I do this?

 Create a symlink from /usr/lib/mozilla/plugins/libflashplayer.so to /usr/lib/opera/plugins/libflashplayer.so[/QUOTE]

Just to make sure, are you looking to create a link in the opera plugins folder that points to the plugin residing within the mozilla directory?

If so,

sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/opera/plugins/libflashplayer.so

If not, and you want it the other way around, just reverse the two paths (so that opera is first, then mozilla).

HTH

---

### Post by jbennett on 2006-02-22
[QUOTE=nrwilk]Also.  Whenever I reinstall, I use this howto to get my java running:

[http://ubuntuforums.org/showthread.php?t=76754](http://ubuntuforums.org/showthread.php?t=76754)

[/QUOTE]

I followed the HOWTO posted here and when I type "java -version" in Terminal, it displays the correct information, but when I attempt to use a website that requires java, it won't work.

Anyone have any ideas about what I might be doing wrong??

Any help is greatly appreciated.
Thanks

---

### Post by kaamos on 2006-02-22
What browser are you using? ff 1.5?

---

### Post by Mark76 on 2006-02-22
I checked mine too and got

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

Does that look right?

---

### Post by nrwilk on 2006-02-22
yup, you got it!

Now go here:
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

If you see the little dancing guy, you've finished successfully!

---

### Post by nrwilk on 2006-02-22
[QUOTE=jbennett]I followed the HOWTO posted here and when I type "java -version" in Terminal, it displays the correct information, but when I attempt to use a website that requires java, it won't work.

Anyone have any ideas about what I might be doing wrong??

Any help is greatly appreciated.
Thanks[/QUOTE]

Did you make sure to use the correct name of the file you downloaded?  It may be different than the filename used in that howto.  So, if it is different and you copied and pasted the commands from the howto directly, then it won't work.  I've done this before too.  Make sure you used the name of the file you downloaded in thos commands instead of just copying and pasting.

---

### Post by jbennett on 2006-02-22
I figured it out.  I had a typing error in one of the ln commands, so the link I created was a dead link and therefore I had installed Java correctly but it was not added as a plugin in firefox.

Thanks for the help though.

---

### Post by nrwilk on 2006-02-22
Is it working in firefox now?

---

### Post by jbennett on 2006-02-22
Yup.  Everything works wonderfully.:)  

I probably just jinxed it. haha.

---

### Post by nrwilk on 2006-02-22
[QUOTE=jbennett]Yup.  Everything works wonderfully.:)  [/QUOTE]
great!

[QUOTE=jbennett]I probably just jinxed it. haha.[/QUOTE]
naw.  You'll be good.

---

### Post by Mark76 on 2006-02-23
I tried to follow the instructions at the Sun site for installing Java on Linux and got this...

---

### Post by Perfect Storm on 2006-02-23
cd /home/mark-williams

---

### Post by Mark76 on 2006-02-23
Ah!

Those <> everyone insists on putting in their instructions confuse the hell out of me :lol:

---

### Post by Mark76 on 2006-02-23
Erm... no :-|

---

### Post by Perfect Storm on 2006-02-23
cd is a command to browse via command line. So you can't browse a file eg. the j2re .bin file.

So the right comman will be
```
cd /home/mark-williams
```

thereafter you can continue to inout the other commands

---

### Post by Mark76 on 2006-02-23
Buggering hell. Could this be any more annoying? :mad:

---

### Post by Perfect Storm on 2006-02-23
Well, I'm bit confused. I have reread the thread (and the other ones about java you made), as I understand you have installed java but want opera to have java too?

---

### Post by Mark76 on 2006-02-23
> Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not locate plug-in 'libnpp.so'.
This executable is included in the install package.


Plug-in path
(Path can be modified in Preferences dialog)

/usr/lib/opera/plugins
/usr/lib/realplay/plugins
/usr/lib/realplay
/usr/lib/mozilla/plugins
/usr/lib/netscape/plugins-libc6

Does that clarify things any? :?

---

### Post by Perfect Storm on 2006-02-23
```
java -version
```

What does it says when you type this comman in thet terminal?

---

### Post by Mark76 on 2006-02-23
It says

> java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)
mark-williams@098786weq:~$


According to Opera my Java path is

---

### Post by Perfect Storm on 2006-02-23
Okay lets start all over:

Download Download JRE 5.0 Update 6 (jre-1_5_0_06-linux-i586.bin file): [https://jsecom16.sun.com/ECom/EComActionServlet;jsessionid=C300ACCAFD54877CE355563E1BACBABA](https://jsecom16.sun.com/ECom/EComActionServlet;jsessionid=C300ACCAFD54877CE355563E1BACBABA)
Save it in /home/mark-williams

```
cd /home/mark-williams
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
sudo update-alternatives --config java

```

When it ask you to choose which java, choose:

**/usr/lib/j2sdk1.5-sun/bin/java**



Java for opera (do this when java is installed):

```
opera
```

**Tools** tab ---> **Preferences**
Pick ** Advanced**  ---> **Content**
and click **Java Options** 

Fill this in the opera box:
**/usr/lib/j2re1.5-sun/lib/i386/**
and press **Validate Java Patch** and press **OK**

restart opera

---

### Post by Perfect Storm on 2006-02-23
[QUOTE=Mark76]It says
```
ava version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)
mark-williams@098786weq:~$
```[/QUOTE]


Okay then read my post above where it says *Java for opera (do this when java is installed):*

---

### Post by Perfect Storm on 2006-02-23
Hmmm...try install java my way then. Works for me.

---

### Post by Mark76 on 2006-02-23
I did as you said.  And it still crashed my browser.

Now, it could be a fault with Ubuntu.  Or Java.  Or the site I'm trying to visit.  Personally I think it's sloppy coding at the site.  But just to be on the safe side give me a link to another site that uses that particular version of runtime.

---

### Post by Perfect Storm on 2006-02-23
Java test site: [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

---

### Post by Mark76 on 2006-02-23
According to the Opera help I need to have openmotif installed.

I've downloaded it, but now when I try to install it using the terminal I can't get super user access with the password that works for synaptic package manager.

WTF? :confused:

---

### Post by Mark76 on 2006-02-23
Well, it works there.  So it's definitely the site in question.

---

### Post by Perfect Storm on 2006-02-23
[QUOTE=Mark76]According to the Opera help I need to have openmotif installed.

I've downloaded it, but now when I try to install it using the terminal I can't get super user access with the password that works for synaptic package manager.

WTF? :confused:[/QUOTE]

Which file is it (package)? terminal output?

---

### Post by Mark76 on 2006-02-23
I have no idea what a terminal output is

---

### Post by Perfect Storm on 2006-02-23
```
cd
sudo dpkg -i openmotif_2.1.30-5_i386.deb

```

apt-get is for installing package from your sourcelist
dpkg is for installing .deb packages you downloaded manually.

---

### Post by Mark76 on 2006-02-23
> mark-williams@098786weq:~$ cd
mark-williams@098786weq:~$ sudo dpkg -i openmotif_2.1.30-5_i386.deb
Password:
Selecting previously deselected package openmotif.
(Reading database ... 86419 files and directories currently installed.)
Unpacking openmotif (from openmotif_2.1.30-5_i386.deb) ...
dpkg: error processing openmotif_2.1.30-5_i386.deb (--install):
 trying to overwrite `/usr/X11R6/bin/mwm', which is also in package motif-clients
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 openmotif_2.1.30-5_i386.deb
mark-williams@098786weq:~$


Sigh :(

---

### Post by Mark76 on 2006-02-23
And in synaptic package manager

> openmotif:

Package openmotif has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


---

### Post by Perfect Storm on 2006-02-23
Do you have motif-clients installed?
Open synapt package manager (Syytem ---> Adminstration ---> Synaptic package manager)

Search button 
and write *motif-clients*

---

### Post by jbmalone on 2006-02-23
I used another tutorial where it had me go download a package out of Synaptic, and when I do java -version, I get the same output other people are getting, but it is not working in Firefox.  Any suggestions?  

Here is a link to that tutorial:

[http://ubuntuforums.org/showthread.php?t=135371&highlight=java+runtime](http://ubuntuforums.org/showthread.php?t=135371&highlight=java+runtime)

---

### Post by Perfect Storm on 2006-02-23
Which version of firefox are you using? The default that came with ubuntu?

---

### Post by jbmalone on 2006-02-23
1.5

---

### Post by Perfect Storm on 2006-02-23
Did you use automatix? Or how and where did you install it?

---

### Post by jbmalone on 2006-02-23
I used this tutorial:
Part 3 - Installing Sun's Java 2 Runtime Environment Plug-in &#8211; for Mozilla Firefox (Internet Browser):

You will probably want to ask again:

Why do I want this Plugin?

Well, if your Ubuntu is NEWLY installed, it does NOT install (by default), this Plugin to be available to your Mozilla Firefox (Internet Browser).

So, launch a window of your Mozilla Firefox browser & go visit the following Internet page:

[http://www.intel.com/products/mother...perl/index.htm](http://www.intel.com/products/mother...perl/index.htm)

The above Internet link takes you to Intel's Internet Site, on a specific Motherboard Page.

Inside that page, you will probably, see that there is a picture that you can NOT view, because you are missing a Plug-in &#8211; the "Sun's Java 2 Runtime Environment" one.

... and you will find a "click here to install plugin" button &#8211; only to find that it can NOT install in this
way...

BUT REMEMBER:
If you install Software with a different method rather than use "Synaptic", there is no go-back (or "Uninstall") option. It's only one way &#8211; & no way back!
Better do it with "Synaptic"...

Launch your "Synaptic Package Manager" program & perform a "Search" for the program "j2re1.4-mozilla-plugin".

Go on & install this program.

Note:
Again, I assume that YOU know how to work with the "Synaptic Package Manager" program.
If NOT (I suggested also before to), go & read My other Tutorial &#8211; Article #: 134914.
Do NOT make me repeat myself...

Then inside your Mozilla Firefox's (Internet Browser) Standard Toolbar, click on the button named "Reload current page" (the equivalent to Internet Explorer's "Refresh" button &#8211; currently NOT "__fresh" but rather "Stinky" & "Rust(y)").

With the Internet Page "Reloaded", now you should be able to VIEW that nice Picture created for "Sun's Java 2 Runtime Environment" Plug-in.

---

### Post by Protostar on 2006-02-23
I am having some problems with Java as well. I know its working and installed because I am running Azureus and Frostwire which both depend on Java. I installed Java Runtime Environment 1.5 using the instructions on the Ubuntu Wiki page. My web browser is Opera, 8.51, and when I open the Preferences window and go to Content Java is alway disabled. I enable it and specify the path to which Java is installed and everything checks out. It says it seems like a valid directory. When I close and restart, and go back the the Preferences windows Java is once again disabled. I don't understand what I am doing wrong.

---

### Post by jbmalone on 2006-02-24
Yeah, I have Azureus running fine too.  I think my problem is that I don't have Firefox recognizing flash as a plugin or something.

---

### Post by jbmalone on 2006-02-25
Any luck on this?

---

### Post by gkiller on 2006-03-11
Hey Artificial Intelligence, I really want to thank you for your easy-to-understand Howto on installing Java and using it in Opera (post #25).

I figured how to install the Sun JRE by myself, but I did not know what to do next (update-alternatives etc..., configuring Opera). Your instructions got Java working for me on Opera immediately :)

So thx again. Ubuntu would be only half as good if there were not all the people helping on the forums :)

---

### Post by rainstreet on 2006-03-12
hope this helps someone, having tried for hours to install java plugin for firefox 1.5 i found a way for it to work for me 

follow the howto changing _05 to _06 
then when you get to install plugins for firefox i did this

cd /opt/firefox/plugins
sudo ln -s /usr/local/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so

then followed the rest of the howto to finish.

to test go here
[http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)

---

