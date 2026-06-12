---
title: "HOW TO get Citrix ICA client working with Google Chrome browser in Linux"
date: 2010-12-14
forum: General Help
---

### Post by eudemus on 2010-12-14
Lots of heartache to find this, but quite simple in the end. Most of the info came from this forum
[http://code.google.com/p/chromium/issues/detail?id=25011#c21](http://code.google.com/p/chromium/issues/detail?id=25011#c21)

But I thought I'd paste / distil / add my comments.

ESSENTIALLY: the trick is that you need to have installed Citrix ICA client (known as XenApp) from Citrix's website, but not use the browser plugin in the way that (say) Firefox does.

Download is available here:
[http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323&productID=-1](http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323&productID=-1)
You want the .deb version, and then use sudo dpkg -i <file location> to install it.

You disable the plugin (which Chrome had presumably installed automatically because I had it on my system for use with Firefox) by entering about:plugins in the address bar in Chrome, and then scroll down to the Citrix plugin and there should be an option to disable it.

It is necessary to setup mime correctly in order for the launch.ica file to be opened with the correct application. 

Chrome uses xdg-open which is a shell script (/usr/bin/xdg-open) which in turn uses gnome-open.  xdg-open comes from xdg-utils, which is distributed by freedesktop.

Gnome-open opens files and urls with the default applications in:
 
 /etc/gnome/defaults.list
 ~.local/share/applications/defaults.list

These lists reference .desktop files.

Creating MIME types for Citrix ICA Client

1. Create new file /usr/share/applications/wfica.desktop

[Desktop Entry]
Name=Citrix ICA client
GenericName=Citrix ICA Client
Comment=Citrix nFuse session file
Categories=Application
Encoding=UTF-8
Exec=/usr/lib/ICAClient/wfica
Icon=wfica
Terminal=false
Type=Application
MimeType=application/x-ica

2. Create new file /usr/share/mime/packages/ica.xml

<?xml version="1.0" encoding="utf-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
<mime-type type="application/x-ica">
<comment>Citrix ICA launcher</comment>
<glob pattern="*.ica"/>
</mime-type>
</mime-info>

3. sudo update-desktop-database && sudo update-mime-database /usr/share/mime



4. Then use your favourite text editor to edit /etc/gnome/defaults.list
and add the line:
application/x-ica=wfica.desktop


5. Run the following from the command line:

xdg-mime install --novendor /usr/share/mime/packages/ica.xml

xdg-mime default wfica.desktop application/x-ica


6. At this point, if you click on a browser link that should launch an application using Citrix, it will download a file called something like "launch.ica". If you click on the little arrow next to this file, and choose "Always open files of this type", then choose "Open", it should work.


I hope this is some help.
Was really tough finding this info via the web. Stumbled over it in the end. I hope this will make a big difference, as I find chrome a much better performing browser these days.

All best, Eudemus

---

### Post by eudemus on 2010-12-14
Half-way down, that should of course read "about [colon] plugins" - let's see if I can get it to do that without it being parsed as an emoticon ...
"about:plugins"

Ho hum!

---

### Post by eudemus on 2010-12-14
Oh well ... I tried!

---

### Post by mma8x on 2010-12-14
worked great for me, thanks! i'm using kubuntu and omitted steps 3 & 4 (didn't work in 3, no such file in 4) without a problem.

---

### Post by BomBom on 2010-12-23
:p

Excellent!
Works great!
Txs a lot

---

### Post by 98cwitr on 2010-12-23
wow....and I've been having to use firefox the whole time :) Thanks!

---

### Post by linuxwonder on 2011-01-08
works great on my laptop (10.04 32bit) but not so well on my desktop(10.04 64bit). Thanks :D

---

### Post by 98cwitr on 2011-01-11
just wanted to say thank you for this! Worked perfectly.

btw, dont worry if this command

```
sudo update-desktop-database && sudo update-mime-database /usr/share/mime
```

has some console output :)

---

### Post by everythingsround on 2011-01-12
Everything worked great for me. Thanks! That was annoying :)

---

### Post by mikowals on 2011-01-13
The steps above worked for me.  Since it took me a while to find this I thought I would post some of the errors that popped up.

Initially launch.ica files were opening with Chrome.  All it took was installing XenApp and making sure the certificate authority files were available in ./usr/lib/ICAClient/keystore/.  I opened several connections but during the process pointed Chrome to wfica to open .ica extension and chose "always open this type of file".

The next day I would get the error "Cannot find section 'ApplicationServers'" and after unchecking "always open this type of file" the files downloaded were not launch.ica but launcher.aspx.

Eudemus instructions in this thread fixed everything.

---

### Post by krul on 2011-02-03
This works for me! Thanks for sharing. :popcorn:

---

### Post by mOOky on 2011-04-04
You ROCK.

:)

I confirm this works on Ubuntu 10.10 running on a netbook.

I installed the .tar.gz version of the ICA installer (v11) from Citrix's site following this guide:

[http://joepcremers.nl/wordpress/connect-to-citrix-access-gateway-on-ubuntu-9-10/](http://joepcremers.nl/wordpress/connect-to-citrix-access-gateway-on-ubuntu-9-10/)

A couple critical items:
1. Install the OpenMotif library.  I'm not sure if the DEB package does this for you.
2. Ensure you download and copy the certificates for your Web Interface site into the ICA client directory.

Both items above are detailed beautifully and simply from the link above.

After following the advice in the referenced thread, I was able to launch in Firefox, but it wasn't until I got the brilliant advice here to disable the plugin and create the MIME mapping that it now happily (and much faster) launches from Chrome.  Many thanks, I'm going back to uninstall Firefox (again).


For extra bonus points, can anyone point me to how to make the RSA SecureID client work in Ubuntu 10.10?

---

### Post by KB8NO on 2011-04-18
This is a simple thing but maybe this will help somebody.  

I'm using Ubuntu 10.10.  I had Open Motif libmotif3 installed previously (did not confirm if this is essential, as stated, since I didn't try Chrome before the library was already installed).  I already had the ICA client installed previously from the tar file and was already using it on Firefox.  I already had certificates transferred into ICA client directory to make Firefox work.

I followed the instructions described and, indeed, launch.ica came up in the box at the bottom with the drop down arrow as described.  However, nothing happened when I tried to open it.  Sadness.

Lots of Goggling did not clear sadness.  However, I followed a hunch.  I picked "show in folder" in the drop down menu and found the launch.ica file in the download directory. I right clicked on the file and opened properties and went to the "open with" tab.  I changed the file association to "Citrix ICA Client Engine (Win32)" and it worked.  Rejoicing.

I too quickly deleted the default association, it was ICA something-or-other, so unfortunately I can't now tell you what Ubuntu decided should be the default file association.  I also can't tell you if this was something unique to my Ubuntu configuration and/or something I may have inadvertently caused from all my messing around with Citrix since I installed 10.10.

Thanks for the postings.

---

### Post by Nobby on 2011-05-23
Just want to say thanks for posting this How to.  Worked for me on 11.04 (using classic gnome desktop) with Chromium.  Had a bit of trouble getting the certificate to work but this post helped: [http://ubuntuforums.org/showthread.php?t=1182355](http://ubuntuforums.org/showthread.php?t=1182355)

---

### Post by TristanL on 2011-05-27
This method works like a charm on Chrome, but in Lubuntu/Chromium you need an additional command to configure Chrome to open Citrix files:

sudo ln -s /usr/bin/gnome-open /usr/local/bin/xdg-open

Read more here:
[http://ubuntuforums.org/showthread.php?t=1499046](http://ubuntuforums.org/showthread.php?t=1499046)

---

### Post by tech-hero on 2011-06-02
I wonder why Citrix doesn't support Google chrome browser out of box after installation. Google Chrome is the most used browser by now. They should do something about this.

---

### Post by eudemus on 2011-06-07
Some extra bits (I'm now using Fedora 14), and some of the above commands fail. I'm thus far just letting them fail, and then I need to do the following at the end.

Once we've got Chrome as far as opening the .ica file with a text editor, simply go into nautilus to the downloads folder, right click on the launch.ica file and choose "Open with ..." and use the option for wfcmgr, remembering to select the check box that tells the system to use this in future for similar files.

I also got a certificate error, and had to get hold of the certificate AddTrustExternalCARoot.crt and put it in
/usr/lib/ICAClient/keystore/cacerts

(Incidentally - a mistake I've often made - step 5. in the original instructions needs to be run as user not as root.)

Much heartache spent over both of these!
Cheers.

---

### Post by eudemus on 2011-06-07
Oh, and in Fedora, the relevant defaults.list files are at:

~/.local/share/applications/
and
/usr/local/share/applications/

Cheers, Eudemus.

---

### Post by garfieldpbj on 2011-10-18
Citrix have launched a new version, which I cannot install on ubuntu 11.04 (I just reinstalled my system) - however the old version works and can be found here: [http://www.citrix.com/English/ss/downloads/details.asp?downloadId=2309164&productId=186&c1=ost1349860#top](http://www.citrix.com/English/ss/downloads/details.asp?downloadId=2309164&productId=186&c1=ost1349860#top) (icaclient_11.100_i386.patched.deb)

/Peter

---

### Post by Malka4re on 2011-10-18
Oh well ... I tried![img]http://www.webcohosting.com/frankaz2.jpg[/img]
[img]http://www.webcohosting.com/myjs.jpg[/img]
[img]http://www.webcohosting.com/frankht.jpg[/img]

---

### Post by nabheet on 2012-01-22
Thank you for these instructions. They helped me connect to my work Citrix system using Chrome on my Ubuntu 11.10.

For all those people who are reporting that Chrome does not download the *.ica file or is showing "Missing Plugin" --> Please ensure that your connection preferences say that your plugin is the "Native Plugin" instead of "Client for Java".

When I logon to citrix, I can go to "Preferences" --> "Connection Preferences". There I can change the plugin.

After you change it to the "Native Plugin", the server will send the *.ica file to Chrome. Or at least that is how it works for me.

Hope this helps.

> **eudemus said:**
> Lots of heartache to find this, but quite simple in the end. Most of the info came from this forum
[http://code.google.com/p/chromium/issues/detail?id=25011#c21](http://code.google.com/p/chromium/issues/detail?id=25011#c21)

But I thought I'd paste / distil / add my comments.

ESSENTIALLY: the trick is that you need to have installed Citrix ICA client (known as XenApp) from Citrix's website, but not use the browser plugin in the way that (say) Firefox does.

Download is available here:
[http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323&productID=-1](http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323&productID=-1)
You want the .deb version, and then use sudo dpkg -i <file location> to install it.

You disable the plugin (which Chrome had presumably installed automatically because I had it on my system for use with Firefox) by entering about:plugins in the address bar in Chrome, and then scroll down to the Citrix plugin and there should be an option to disable it.

It is necessary to setup mime correctly in order for the launch.ica file to be opened with the correct application. 

Chrome uses xdg-open which is a shell script (/usr/bin/xdg-open) which in turn uses gnome-open.  xdg-open comes from xdg-utils, which is distributed by freedesktop.

Gnome-open opens files and urls with the default applications in:
 
 /etc/gnome/defaults.list
 ~.local/share/applications/defaults.list

These lists reference .desktop files.

Creating MIME types for Citrix ICA Client

1. Create new file /usr/share/applications/wfica.desktop

[Desktop Entry]
Name=Citrix ICA client
GenericName=Citrix ICA Client
Comment=Citrix nFuse session file
Categories=Application
Encoding=UTF-8
Exec=/usr/lib/ICAClient/wfica
Icon=wfica
Terminal=false
Type=Application
MimeType=application/x-ica

2. Create new file /usr/share/mime/packages/ica.xml

<?xml version="1.0" encoding="utf-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
<mime-type type="application/x-ica">
<comment>Citrix ICA launcher</comment>
<glob pattern="*.ica"/>
</mime-type>
</mime-info>

3. sudo update-desktop-database && sudo update-mime-database /usr/share/mime



4. Then use your favourite text editor to edit /etc/gnome/defaults.list
and add the line:
application/x-ica=wfica.desktop


5. Run the following from the command line:

xdg-mime install --novendor /usr/share/mime/packages/ica.xml

xdg-mime default wfica.desktop application/x-ica


6. At this point, if you click on a browser link that should launch an application using Citrix, it will download a file called something like "launch.ica". If you click on the little arrow next to this file, and choose "Always open files of this type", then choose "Open", it should work.


I hope this is some help.
Was really tough finding this info via the web. Stumbled over it in the end. I hope this will make a big difference, as I find chrome a much better performing browser these days.

All best, Eudemus

---

### Post by Motozenmaster on 2012-02-09
Followed instructions implicitly.  Doesn't work for me on Ubuntu 11.10 64-bit.  ICA file opens but does nothing. I received no error messages or saw anything unusual during installation process. Client works on Firefox though. Any other ideas?

---

### Post by dmadiedo on 2012-02-11
Mmmm, probably its because the receiver is not properly configured. Have you tried to execute first /opt/Citrix/ICAClient/wfcmgr, o /usr/lib/ICAClient/wfcmgr? (it depends on the client version you installed.

---

### Post by Motozenmaster on 2012-02-13
> **dmadiedo said:**
> Mmmm, probably its because the receiver is not properly configured. Have you tried to execute first /opt/Citrix/ICAClient/wfcmgr, o /usr/lib/ICAClient/wfcmgr? (it depends on the client version you installed.


My result is: /opt/Citrix/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.4: wrong ELF class: ELFCLASS64

I have no idea what this means. Perhaps you do?

---

### Post by natrixgli on 2012-02-21
> **Motozenmaster said:**
> My result is: /opt/Citrix/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.4: wrong ELF class: ELFCLASS64

I have no idea what this means. Perhaps you do?

This is because you have the 64-bit version of libmotif4 installed. You can install the 32-bit version and create a symbolic link to it instead per this:

[http://kenfallon.com/to-me-six-months-from-now-how-to-get-citrix-running-on-debian-sid-amd64/]("http://kenfallon.com/to-me-six-months-from-now-how-to-get-citrix-running-on-debian-sid-amd64/")

---

### Post by Motozenmaster on 2012-02-22
> **natrixgli said:**
> This is because you have the 64-bit version of libmotif4 installed. You can install the 32-bit version and create a symbolic link to it instead per this:

[http://kenfallon.com/to-me-six-months-from-now-how-to-get-citrix-running-on-debian-sid-amd64/]("http://kenfallon.com/to-me-six-months-from-now-how-to-get-citrix-running-on-debian-sid-amd64/")
No can do.  I get the following:

XXXXXXXXXXXXXXXXXXX:~/Downloads$ sudo dpkg -i --force-architecture libmotif*i386.deb
Selecting previously deselected package libmotif3:i386.
dpkg: regarding libmotif3_2.2.3-4_i386.deb containing libmotif3:i386:
 libmotif4 conflicts with libmotif3
  libmotif3:i386 (version 2.2.3-4) is to be installed.
dpkg: error processing libmotif3_2.2.3-4_i386.deb (--install):
 conflicting packages - not installing libmotif3:i386
Errors were encountered while processing:
 libmotif3_2.2.3-4_i386.deb

---

### Post by cu_ on 2012-03-20
Thanks for posting this.  This got me over the last bump in running citrix client from ubuntu.  So thankful.

---

### Post by MainVoid on 2012-04-04
Newer versions (well, I've honestly only tried the latest one, 12.0.0) of the Citrix Receiver installs the package in a different directory structure than used in the .desktop file here.

Replace:

Exec=/usr/lib/ICAClient/wfica

With:

Exec=/opt/Citrix/ICAClient/wfica

Above made things work for me properly ...

---

### Post by openick on 2012-04-11
I have citrix ICA working well, following these instructions, but I am unable to upload files from my computer to the citrix environment nor download files from within the citrix environment to my computer. The "Choose a file to upload" window shows a computer icon, but does not show the directory structure. In the top navigation window of this file upload window, the Computer ICON is present, but the drop down is a blank list.

On the left there are also icons such as Favorites, Downloads and Libraries, but clicking on these icons shows the following error message:

"Restrictions:  The operation has been cancelled due to restriction in effect on this computer. Please contact your system administrator"

What do I need to do to upload files from my computer to the Citrix ICA client?  I am filling up a form that requires attachments to be uploaded.

Thank you.

---

### Post by jajodo on 2013-01-19
Wow.  Thanks to all.  This works for me on 12.10 64 bit perfectly.  As stated above I needed to use the opt directory though.  I will rehash the change so others don't have to scroll back and forth through the responses:

1. Create new file /usr/share/applications/wfica.desktop

[Desktop Entry]
Name=Citrix ICA client
GenericName=Citrix ICA Client
Comment=Citrix nFuse session file
Categories=Application
Encoding=UTF-8
Exec=/opt/Citrix/ICAClient/wfica
Icon=wfica
Terminal=false
Type=Application
MimeType=application/x-ica

2. Create new file /usr/share/mime/packages/ica.xml

<?xml version="1.0" encoding="utf-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
<mime-type type="application/x-ica">
<comment>Citrix ICA launcher</comment>
<glob pattern="*.ica"/>
</mime-type>
</mime-info>

3. sudo update-desktop-database && sudo update-mime-database /usr/share/mime

4. Then use your favourite text editor to edit /etc/gnome/defaults.list
and add the line:
application/x-ica=wfica.desktop

5. Run the following from the command line:

xdg-mime install --novendor /usr/share/mime/packages/ica.xml

xdg-mime default wfica.desktop application/x-ica

---

### Post by 98cwitr on 2013-05-02
Awesomeness! Last post works like a charm...I just have to click on the ICA file. Firefox automatically opens it...ceste la vie

---

