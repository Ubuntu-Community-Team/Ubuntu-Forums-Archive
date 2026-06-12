---
title: "Cannot find 7Zip in order to unzip new downloads"
date: 2010-08-07
forum: General Help
---

### Post by marcus_lancashire on 2010-08-07
Ubuntu 10.04 LTS - the Lucid Lynx
Dual Boot with Windwos Vista
Level - beginner (started today 07/0810)

Hello
I have just given Linux a try for the first time and so far its not proving to be a good experience. I have so far just tried to install a couple of basic programs I am familiar with and ones suggested by Lifehacker.

I wanted to install Tweetdeck, which meant installing Adobe Air. I duly downloaded Adobe Air but it then says I need to choose an application to open it. Assuming that the bin file was a zip file I looked in the software centre and found 7zip. Told it to load that but then couldn't find where it was. Its not listed in the Applications drop down (top right) so I found 'search for a file' and entered *7zip* to be shown 5 files. All but one appear to be a form of image file the other (7zip.desktop) isn't an exe either. Double clicking on it just gets me the following in something called gedit.

Name=7zip
Comment=7zip compression/uncompression tool
Terminal=false
Type=Application
Categories=Application;Utility;
MimeType=application/x-7zip-compressed
X-AppInstall-Package=p7zip-full
X-AppInstall-Popcon=30423
X-AppInstall-Section=universe
X-Ubuntu-Gettext-Domain=app-install-data

I then gave up and used google to find the program and download it, but just came across the same problem. Why oh why is there not some default program already loaded for unzipping files? How can I find 7Zip (I have already looked in the bin folder on the system drive but nothing there) and run it to tell it to make itself the default for unzipping files?

So far things seem to be more difficult than on windows, although it may simply be that I am so used to Windows.

---

### Post by stoneage on 2010-08-07
7zip is a command line application, it doesn't have a gui. Right click on the file and select 'extract here'.

One question though, you say you 'assume' the bin file is a .zip........so did you look and see? You can already extract .zip, you need 7zip for .7z files.

---

### Post by xXxBlender3DxXx on 2010-08-07
.bin files are binaries. Right click on them, go to Permissions, and check the "executable" option. Then, go to Terminal (Accessories -> Terminal), cd to the directory, and run:

```
sudo sh ./NAME OF FILE
```

Have fun!

Also, installing 7zip and WinRAR actually just installs the compression/extraction algorithms (command line). File Roller is the only GUI you ever will need to use.

---

### Post by xXxBlender3DxXx on 2010-08-07
Can anybody tell me how to delete posts? I feel really stupid...

---

### Post by Ginsu543 on 2010-08-07
> **marcus_lancashire said:**
> 
So far things seem to be more difficult than on windows, although it may simply be that I am so used to Windows.
This may be quite truer than you realize. Don't give up! :) Linux does have a learning curve but so did Windows. You just don't remember because you're so used to it now.

If you are trying to unzip .zip files in Ubuntu, you don't need 7zip. There IS a native decompression tool already inherent in the OS. Just right click on the .zip file and choose "Extract Here" in the context menu. That should unpack the .zip file for you.

As for installing Tweetdeck, check out [_this site_](http://www.kartook.com/2010/07/how-ot-install-tweetdeck-on-ubuntu-10-04-64bit/) and [_this site_](http://data.agaric.com/node/3062).

Hope that helps.

---

### Post by happyhamster on 2010-08-07
> **marcus_lancashire said:**
> I wanted to install Tweetdeck, which meant installing Adobe Air. I duly downloaded Adobe Air but it then says I need to choose an application to open it. Assuming that the bin file was a zip file I looked in the software centre and found 7zip. Told it to load that but then couldn't find where it was.
It's probably in /usr/bin/ but that's not really relevant. After installing that package, its tools are directly available from the command-line (Applications-->Accessories-->Terminal, and from there you can run 7z or 7za I believe). After installing the package, 7zip support should also be integrated into your archive manager (so you can just right-click a file from within your file-manager, and choose "Extract Here").

> 
 Its not listed in the Applications drop down (top right) so I found 'search for a file' and entered *7zip* to be shown 5 files. All but one appear to be a form of image file the other (7zip.desktop) isn't an exe either. Double clicking on it just gets me the following in something called gedit.

There's no need to hunt for files: the tools you install are either directly available in a terminal (doesn't matter which folder you are in), or are given a place in the Main Menu (for graphical applications). In this case you installed some low-level tools that don't have a graphical interface.

> I then gave up and used google to find the program and download it, but just came across the same problem. Why oh why is there not some default program already loaded for unzipping files?
I think because quite a lot of them are (partly) closed source, and there could be legal (licensing) issues if those tools are part of a default install. Same thing for media codecs and so on.

>  How can I find 7Zip (I have already looked in the bin folder on the system drive but nothing there) and run it to tell it to make itself the default for unzipping files?
Your archive manager will take care of that automatically. If you right-click the file you want to extract and there is an "Extract Here" option, then all's well. If not, try opening the file in the archive manager manually: right-click the file, choose "Open with Other Application"-->Archive Manager. It will probably fail though, because I don't think the file is an archive.

> 
So far things seem to be more difficult than on windows, although it may simply be that I am so used to Windows.
I expect that manually-installing-an-Adobe-product-on-a-Linux-box is one of the more difficult things to do actually. If possible at all that is :)

Anyway, if you are running a 32 bit version of Ubuntu, try downloading the .deb version of the installer (that's the native file format for packages on Ubuntu): just double-click it and the installer should start.

If you're using a 64 bits version of Ubuntu, then things get complicated really quick, because Adobe doesn't do 64 bits AIR. See:

[http://kb2.adobe.com/cps/408/kb408084.html#main_Installing_AIR_1.5_on_64-bit_Ubuntu_7.10__8.04_and_9.04](http://kb2.adobe.com/cps/408/kb408084.html#main_Installing_AIR_1.5_on_64-bit_Ubuntu_7.10__8.04_and_9.04)

That will be no fun.

---

### Post by marcus_lancashire on 2010-08-07
Thank you all for your help, I have moved back to windows now for the rest of the evening but will certainly use your excellent information to solve my little trouble tomorrow.

Thanks again
Marcus

---

