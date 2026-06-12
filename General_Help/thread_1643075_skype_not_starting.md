---
title: "skype not starting"
date: 2010-12-11
forum: General Help
---

### Post by SnoopNL on 2010-12-11
Hello,

Skype is not starting at all at my system.
When I start skype a little hdd activity is there, but after that nothing.
No splash , no screen of skype , nothing.

I tried reinstalling skype but that does not seem to work for me.

Does anyone have a suggestion?

It worked perfectly before updating my system and installing SIPE for pidgin.

I get this error in my root terminal :
skype: symbol lookup error: /usr/lib32/libQtNetwork.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

please advise.

---

### Post by HermanAB on 2010-12-11
Howdy,

Open a console and see whether Skype is already running (but crashed):
$ ps -e | grep skype

If so, kill it:
$ sudo killall skype

Then run it again and look at the error messages:
$ skype

If all else fails, install the 'Static' version of Skype from the Skype web site.

---

### Post by SnoopNL on 2010-12-11
> **HermanAB said:**
> Howdy,

Open a console and see whether Skype is already running (but crashed):
$ ps -e | grep skype

If so, kill it:
$ sudo killall skype

Then run it again and look at the error messages:
$ skype

If all else fails, install the 'Static' version of Skype from the Skype web site.

Hello,

Thank you for your help.
However, the problem still persists.

Any suggestions?
Skype was btw not running at all.

btw2, same error.

update 2:
I tried purging and cleaning skype as well as skype-static.
Tried to reinstall libqt4-network but still the same issue.

Any suggestions?

---

### Post by HermanAB on 2010-12-11
So, when you run skype from the command line, you don't get any error messages?  If true, then use Ekiga, otherwise, fix whatever Skype is complaining about.

---

### Post by SnoopNL on 2010-12-11
> **HermanAB said:**
> So, when you run skype from the command line, you don't get any error messages?  If true, then use Ekiga, otherwise, fix whatever Skype is complaining about.

If skype was working, would i post here? :)

I need **help** fixing the issue with skype with the error i posted in my first post here.

Because reinstall what it asks for does not resolve my issue.

The error posted is the error from the terminal.

---

### Post by vangop on 2010-12-11
How did you install? I just installed a fresh system and installed the skype via synaptic - works fine.
I saw some ppl installing prereqs via synaptic and the skype itself from the skype site. If you did the same - try synaptic.

---

### Post by SnoopNL on 2010-12-11
> **vangop said:**
> How did you install? I just installed a fresh system and installed the skype via synaptic - works fine.
I saw some ppl installing prereqs via synaptic and the skype itself from the skype site. If you did the same - try synaptic.

Both options were tried.
Same issue appears.


System has been up and running foe 3 days now.

---

### Post by pytheas22 on 2010-12-11
Have you seen this [bug report]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/271550")?  I found it by googling the error message you get when trying to start skype.  I would try manually installing the libraries it complains about using the commands in posts #6 and #9 of the bug report.

If this doesn't help you, what is the output of:

```
ldd /usr/bin/skype
```

---

### Post by SnoopNL on 2010-12-11
> **pytheas22 said:**
> Have you seen this [bug report]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/271550")?  I found it by googling the error message you get when trying to start skype.  I would try manually installing the libraries it complains about using the commands in posts #6 and #9 of the bug report.

If this doesn't help you, what is the output of:

```
ldd /usr/bin/skype
```

Hello,

It seems it is 404'ing on me , i mean the wget commands in the posts.

the ldd gives out this:

    linux-gate.so.1 =>  (0xf776e000)
    libasound.so.2 => /usr/lib32/libasound.so.2 (0xf768b000)
    libXv.so.1 => /usr/lib32/libXv.so.1 (0xf7685000)
    libXss.so.1 => /usr/lib32/libXss.so.1 (0xf7680000)
    librt.so.1 => /lib32/librt.so.1 (0xf7677000)
    libQtDBus.so.4 => /usr/lib32/libQtDBus.so.4 (0xf75fc000)
    libQtGui.so.4 => /usr/lib/eToken/libQtGui.so.4 (0xf6e9c000)
    libQtNetwork.so.4 => /usr/lib32/libQtNetwork.so.4 (0xf6d74000)
    libQtCore.so.4 => /usr/lib/eToken/libQtCore.so.4 (0xf6be4000)
    libpthread.so.0 => /lib32/libpthread.so.0 (0xf6bcb000)
    libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf6ae0000)
    libm.so.6 => /lib32/libm.so.6 (0xf6aba000)
    libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf6a9e000)
    libc.so.6 => /lib32/libc.so.6 (0xf6944000)
    libdl.so.2 => /lib32/libdl.so.2 (0xf693f000)
    libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6822000)
    libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6812000)
    /lib/ld-linux.so.2 (0xf776f000)
    libQtXml.so.4 => /usr/lib/eToken/libQtXml.so.4 (0xf67cb000)
    libpng12.so.0 => /lib32/libpng12.so.0 (0xf67a6000)
    libSM.so.6 => /usr/lib32/libSM.so.6 (0xf679c000)
    libICE.so.6 => /usr/lib32/libICE.so.6 (0xf6783000)
    libz.so.1 => /usr/lib32/libz.so.1 (0xf676e000)
    libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf6769000)
    libglib-2.0.so.0 => /lib32/libglib-2.0.so.0 (0xf669a000)
    libXi.so.6 => /usr/lib32/libXi.so.6 (0xf668c000)
    libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6681000)
    libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf6679000)
    libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf6673000)
    libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf6669000)
    libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf6665000)
    libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf65ed000)
    libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf65bd000)
    libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf65a3000)
    libuuid.so.1 => /lib32/libuuid.so.1 (0xf659e000)
    libpcre.so.3 => /lib32/libpcre.so.3 (0xf6568000)
    libexpat.so.1 => /lib32/libexpat.so.1 (0xf6541000)
    libXau.so.6 => /usr/lib32/libXau.so.6 (0xf653d000)
    libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6537000)


I tried that post already , i should have mentioned i googled for it.

---

### Post by pytheas22 on 2010-12-11
> 	
Re: skype not starting
Quote:
Originally Posted by pytheas22 View Post
Have you seen this bug report? I found it by googling the error message you get when trying to start skype. I would try manually installing the libraries it complains about using the commands in posts #6 and #9 of the bug report.

If this doesn't help you, what is the output of:

Code:

ldd /usr/bin/skype

Hello,

It seems it is 404'ing on me , i mean the wget commands in the posts.

the ldd gives out this:

linux-gate.so.1 => (0xf776e000)
libasound.so.2 => /usr/lib32/libasound.so.2 (0xf768b000)
libXv.so.1 => /usr/lib32/libXv.so.1 (0xf7685000)
libXss.so.1 => /usr/lib32/libXss.so.1 (0xf7680000)...

It doesn't actually look like the missing libraries are the problem, since ldd doesn't seem to complain.

I wonder if you have multiple, conflicting copies of these libraries installed.  What is the output of:

```
sudo updatedb
locate libQtNetwork.so.4
```

Multiple copies of the same library seems to have been the issue for [this poster]("http://osdir.com/ml/ubuntu-users/2009-06/msg00857.html").

---

### Post by SnoopNL on 2010-12-11
> **pytheas22 said:**
> It doesn't actually look like the missing libraries are the problem, since ldd doesn't seem to complain.

I wonder if you have multiple, conflicting copies of these libraries installed.  What is the output of:

```
sudo updatedb
locate libQtNetwork.so.4
```Multiple copies of the same library seems to have been the issue for [this poster]("http://osdir.com/ml/ubuntu-users/2009-06/msg00857.html").

Seems you are right on this one:
/usr/lib/libQtNetwork.so.4
/usr/lib/libQtNetwork.so.4.7
/usr/lib/libQtNetwork.so.4.7.0
/usr/lib32/libQtNetwork.so.4
/usr/lib32/libQtNetwork.so.4.7
/usr/lib32/libQtNetwork.so.4.7.0


But how to remove not needed copies?

---

### Post by pytheas22 on 2010-12-11
Ah, well, at least we're (hopefully) on the right track.

I assume you could just delete the unnecessary copies of the libraries (or, to be safe, move them to some other location until you're sure you don't need them).  It sounds like that's what worked for the person in the thread I linked to.  So something like this should work (copying the three libQtNetwork.so.4* files under /usr/lib to /root, where you can keep them in case you need them again later):

```
sudo mv /usr/lib/libQtNetwork.so.4* /root

```

If that doesn't do it, try replacing these three files back into /usr/lib and cleaning out the ones in /usr/lib32 instead--I am not sure which copies of the libraries are the "good" ones.

Also, you might have to do this not just for the libQtNetwork.so.4* files, but for the other libQt files as well; I'm not sure.

You seem to have a good handle of things and I assume you're comfortable on the command line, but if you're not sure what to do and would like this all explained more thoroughly, let me know.

---

### Post by SnoopNL on 2010-12-11
Hello,

First of all, thank you for the help.
It is really helpfull and nice to see that there is support.

I ussually administrate Windows env. so I am not that familiar with Linux (specially not Debian based).

The problem arises that it seems to not find the LibQtNetwork.so.4 when i try to move it.

This is what i get if i locate the LibQtNetwork.so.4
/root/libQtNetwork.so.4
/root/libQtNetwork.so.4.7
/root/libQtNetwork.so.4.7.0
/usr/lib32/libQtNetwork.so.4
/usr/lib32/libQtNetwork.so.4.7
/usr/lib32/libQtNetwork.so.4.7.0

i tried the commandline like this:
[B]/root/libQtNetwork.so.4
/root/libQtNetwork.so.4.7
/root/libQtNetwork.so.4.7.0
/usr/lib32/libQtNetwork.so.4
/usr/lib32/libQtNetwork.so.4.7
/usr/lib32/libQtNetwork.so.4.7.0
[/B]
/root/libQtNetwork.so.4
/root/libQtNetwork.so.4.7
/root/libQtNetwork.so.4.7.0
/usr/lib32/libQtNetwork.so.4
/usr/lib32/libQtNetwork.so.4.7
/usr/lib32/libQtNetwork.so.4.7.0

So I tried:

root@Prime:/# mv /usr/lib/libQtNetwork.so.4* /root

I then get:
mv: cannot stat `/usr/lib/libQtNetwork.so.4*': No such file or directory

Edit:
Maybe this is handier:
root@Prime:/tmp/skype# skype
skype: error while loading shared libraries: libQtNetwork.so.4: cannot open shared object file: No such file or directory
root@Prime:/tmp/skype# sudo mv /usr/lib32/libQtNetwork.so.4.7 /root
mv: cannot stat `/usr/lib32/libQtNetwork.so.4.7': No such file or directory
root@Prime:/tmp/skype# sudo mv /usr/lib32/libQtNetwork* /root
root@Prime:/tmp/skype# locate libQtNetwork.so.4
/root/libQtNetwork.so.4
/root/libQtNetwork.so.4.7
/root/libQtNetwork.so.4.7.0
/usr/lib32/libQtNetwork.so.4
/usr/lib32/libQtNetwork.so.4.7
/usr/lib32/libQtNetwork.so.4.7.0
root@Prime:/tmp/skype# sudo rm /usr/lib32/libQtNetwork.so.4.7* /root
rm: cannot remove `/usr/lib32/libQtNetwork.so.4.7*': No such file or directory
rm: cannot remove `/root': Is a directory
root@Prime:/tmp/skype# sudo rm /usr/lib/libQtNetwork.so.4.7* /root
rm: cannot remove `/usr/lib/libQtNetwork.so.4.7*': No such file or directory
rm: cannot remove `/root': Is a directory
root@Prime:/tmp/skype# sudo rm /usr/lib/libQtNetwork.so.4.7*
rm: cannot remove `/usr/lib/libQtNetwork.so.4.7*': No such file or directory
root@Prime:/tmp/skype# sudo mv /root/lib/libQtNetwork.so.4* /ill
mv: cannot stat `/root/lib/libQtNetwork.so.4*': No such file or directory
root@Prime:/tmp/skype# locate libQtNetwork.so.4
/root/libQtNetwork.so.4
/root/libQtNetwork.so.4.7
/root/libQtNetwork.so.4.7.0
/usr/lib32/libQtNetwork.so.4
/usr/lib32/libQtNetwork.so.4.7
/usr/lib32/libQtNetwork.so.4.7.0
root@Prime:/tmp/skype# sudo mv /root/LibQtNetwork.so.4* /ill
mv: cannot stat `/root/LibQtNetwork.so.4*': No such file or directory
root@Prime:/tmp/skype# cd ..
root@Prime:/tmp# cd ..
root@Prime:/# cd lib
root@Prime:/lib# cd ..
root@Prime:/# sudo mv /root/LibQtNetwork.so.4* /ill
mv: cannot stat `/root/LibQtNetwork.so.4*': No such file or directory
root@Prime:/# sudo mv /LibQtNetwork.so.4* /ill
mv: cannot stat `/LibQtNetwork.so.4*': No such file or directory
root@Prime:/# sudo mv /lib/LibQtNetwork.so.4* /ill
mv: cannot stat `/lib/LibQtNetwork.so.4*': No such file or directory

Seems I am just getting more stupid by the day :).

---

### Post by pytheas22 on 2010-12-11
Don't worry, it's complicated stuff!  Probably some of the files are symbolic links and the mv command might not like that--I should have thought about this before.

So let's see which files we're actually dealing with.  What is the output of:
```

ls -l /usr/lib32/libQt*
ls -l /usr/lib/libQt*
```

---

### Post by SnoopNL on 2010-12-11
> **pytheas22 said:**
> Don't worry, it's complicated stuff!  Probably some of the files are symbolic links and the mv command might not like that--I should have thought about this before.

So let's see which files we're actually dealing with.  What is the output of:
```

ls -l /usr/lib32/libQt*
ls -l /usr/lib/libQt*
```

Ok here it is
Output ls -l /usr/lib32/libQt*:
lrwxrwxrwx 1 root root       18 2010-12-11 17:26 /usr/lib32/libQt3Support.so -> libQt3Support.so.4
lrwxrwxrwx 1 root root       22 2010-12-11 17:26 /usr/lib32/libQt3Support.so.4 -> libQt3Support.so.4.7.0
lrwxrwxrwx 1 root root       22 2010-12-11 17:26 /usr/lib32/libQt3Support.so.4.7 -> libQt3Support.so.4.7.0
-rw-r--r-- 1 root root  2997592 2010-10-03 10:41 /usr/lib32/libQt3Support.so.4.7.0
lrwxrwxrwx 1 root root       17 2010-12-11 17:26 /usr/lib32/libQtCLucene.so -> libQtCLucene.so.4
lrwxrwxrwx 1 root root       21 2010-12-11 17:26 /usr/lib32/libQtCLucene.so.4 -> libQtCLucene.so.4.7.0
lrwxrwxrwx 1 root root       21 2010-12-11 17:26 /usr/lib32/libQtCLucene.so.4.7 -> libQtCLucene.so.4.7.0
-rw-r--r-- 1 root root   969024 2010-10-03 10:41 /usr/lib32/libQtCLucene.so.4.7.0
lrwxrwxrwx 1 root root       16 2010-12-11 17:26 /usr/lib32/libQtCore.so -> libQtCore.so.4.7
lrwxrwxrwx 1 root root       18 2010-12-11 17:26 /usr/lib32/libQtCore.so.4 -> libQtCore.so.4.7.0
lrwxrwxrwx 1 root root       18 2010-12-11 17:26 /usr/lib32/libQtCore.so.4.7 -> libQtCore.so.4.7.0
-rw-r--r-- 1 root root  2714428 2010-10-03 10:41 /usr/lib32/libQtCore.so.4.7.0
lrwxrwxrwx 1 root root       14 2010-12-11 17:26 /usr/lib32/libQtDBus.so -> libQtDBus.so.4
lrwxrwxrwx 1 root root       18 2010-12-11 17:26 /usr/lib32/libQtDBus.so.4 -> libQtDBus.so.4.7.0
lrwxrwxrwx 1 root root       18 2010-12-11 17:26 /usr/lib32/libQtDBus.so.4.7 -> libQtDBus.so.4.7.0
-rw-r--r-- 1 root root   502312 2010-10-03 10:41 /usr/lib32/libQtDBus.so.4.7.0
lrwxrwxrwx 1 root root       15 2010-12-11 17:26 /usr/lib32/libQtGui.so -> libQtGui.so.4.7
lrwxrwxrwx 1 root root       17 2010-12-11 17:26 /usr/lib32/libQtGui.so.4 -> libQtGui.so.4.7.0
lrwxrwxrwx 1 root root       17 2010-12-11 17:26 /usr/lib32/libQtGui.so.4.7 -> libQtGui.so.4.7.0
-rw-r--r-- 1 root root 11298492 2010-10-03 10:41 /usr/lib32/libQtGui.so.4.7.0
lrwxrwxrwx 1 root root       18 2010-12-11 17:26 /usr/lib32/libQtOpenGL.so -> libQtOpenGL.so.4.7
lrwxrwxrwx 1 root root       20 2010-12-11 17:26 /usr/lib32/libQtOpenGL.so.4 -> libQtOpenGL.so.4.7.0
lrwxrwxrwx 1 root root       20 2010-12-11 17:26 /usr/lib32/libQtOpenGL.so.4.7 -> libQtOpenGL.so.4.7.0
-rw-r--r-- 1 root root   929560 2010-10-03 10:41 /usr/lib32/libQtOpenGL.so.4.7.0
lrwxrwxrwx 1 root root       16 2010-12-11 17:26 /usr/lib32/libQtScript.so -> libQtScript.so.4
lrwxrwxrwx 1 root root       20 2010-12-11 17:26 /usr/lib32/libQtScript.so.4 -> libQtScript.so.4.7.0
lrwxrwxrwx 1 root root       20 2010-12-11 17:26 /usr/lib32/libQtScript.so.4.7 -> libQtScript.so.4.7.0
-rw-r--r-- 1 root root  2599972 2010-10-03 10:41 /usr/lib32/libQtScript.so.4.7.0
lrwxrwxrwx 1 root root       21 2010-12-11 17:26 /usr/lib32/libQtScriptTools.so -> libQtScriptTools.so.4
lrwxrwxrwx 1 root root       25 2010-12-11 17:26 /usr/lib32/libQtScriptTools.so.4 -> libQtScriptTools.so.4.7.0
lrwxrwxrwx 1 root root       25 2010-12-11 17:26 /usr/lib32/libQtScriptTools.so.4.7 -> libQtScriptTools.so.4.7.0
-rw-r--r-- 1 root root   777936 2010-10-03 10:41 /usr/lib32/libQtScriptTools.so.4.7.0
lrwxrwxrwx 1 root root       13 2010-12-11 17:26 /usr/lib32/libQtSql.so -> libQtSql.so.4
lrwxrwxrwx 1 root root       17 2010-12-11 17:26 /usr/lib32/libQtSql.so.4 -> libQtSql.so.4.7.0
lrwxrwxrwx 1 root root       17 2010-12-11 17:26 /usr/lib32/libQtSql.so.4.7 -> libQtSql.so.4.7.0
-rw-r--r-- 1 root root   251864 2010-10-03 10:41 /usr/lib32/libQtSql.so.4.7.0
lrwxrwxrwx 1 root root       15 2010-12-11 17:26 /usr/lib32/libQtSvg.so -> libQtSvg.so.4.7
lrwxrwxrwx 1 root root       17 2010-12-11 17:26 /usr/lib32/libQtSvg.so.4 -> libQtSvg.so.4.7.0
lrwxrwxrwx 1 root root       17 2010-12-11 17:26 /usr/lib32/libQtSvg.so.4.7 -> libQtSvg.so.4.7.0
-rw-r--r-- 1 root root   355292 2010-10-03 10:41 /usr/lib32/libQtSvg.so.4.7.0
lrwxrwxrwx 1 root root       14 2010-12-11 17:26 /usr/lib32/libQtTest.so -> libQtTest.so.4
lrwxrwxrwx 1 root root       18 2010-12-11 17:26 /usr/lib32/libQtTest.so.4 -> libQtTest.so.4.7.0
lrwxrwxrwx 1 root root       18 2010-12-11 17:26 /usr/lib32/libQtTest.so.4.7 -> libQtTest.so.4.7.0
-rw-r--r-- 1 root root   141352 2010-10-03 10:41 /usr/lib32/libQtTest.so.4.7.0
lrwxrwxrwx 1 root root       21 2010-12-11 17:26 /usr/lib32/libQtXmlPatterns.so -> libQtXmlPatterns.so.4
lrwxrwxrwx 1 root root       25 2010-12-11 17:26 /usr/lib32/libQtXmlPatterns.so.4 -> libQtXmlPatterns.so.4.7.0
lrwxrwxrwx 1 root root       25 2010-12-11 17:26 /usr/lib32/libQtXmlPatterns.so.4.7 -> libQtXmlPatterns.so.4.7.0
-rw-r--r-- 1 root root  4385680 2010-10-03 10:38 /usr/lib32/libQtXmlPatterns.so.4.7.0
lrwxrwxrwx 1 root root       15 2010-12-11 17:26 /usr/lib32/libQtXml.so -> libQtXml.so.4.7
lrwxrwxrwx 1 root root       17 2010-12-11 17:26 /usr/lib32/libQtXml.so.4 -> libQtXml.so.4.7.0
lrwxrwxrwx 1 root root       17 2010-12-11 17:26 /usr/lib32/libQtXml.so.4.7 -> libQtXml.so.4.7.0
-rw-r--r-- 1 root root   272192 2010-10-03 10:41 /usr/lib32/libQtXml.so.4.7.0


And here is the output of ls -l /usr/lib/libQt*
lrwxrwxrwx 1 root root       21 2010-12-11 17:22 /usr/lib/libQtCLucene.so.4 -> libQtCLucene.so.4.7.0
lrwxrwxrwx 1 root root       21 2010-12-11 17:22 /usr/lib/libQtCLucene.so.4.7 -> libQtCLucene.so.4.7.0
-rw-r--r-- 1 root root  1036144 2010-11-19 17:51 /usr/lib/libQtCLucene.so.4.7.0
lrwxrwxrwx 1 root root       18 2010-12-11 17:22 /usr/lib/libQtCore.so.4 -> libQtCore.so.4.7.0
lrwxrwxrwx 1 root root       18 2010-12-11 17:22 /usr/lib/libQtCore.so.4.7 -> libQtCore.so.4.7.0
-rw-r--r-- 1 root root  2732832 2010-11-19 17:51 /usr/lib/libQtCore.so.4.7.0
lrwxrwxrwx 1 root root       18 2010-12-11 17:21 /usr/lib/libQtDBus.so.4 -> libQtDBus.so.4.7.0
lrwxrwxrwx 1 root root       18 2010-12-11 17:21 /usr/lib/libQtDBus.so.4.7 -> libQtDBus.so.4.7.0
-rw-r--r-- 1 root root   504184 2010-11-19 17:51 /usr/lib/libQtDBus.so.4.7.0
lrwxrwxrwx 1 root root       32 2010-12-11 17:21 /usr/lib/libQtDesignerComponents.so.4 -> libQtDesignerComponents.so.4.7.0
lrwxrwxrwx 1 root root       32 2010-12-11 17:21 /usr/lib/libQtDesignerComponents.so.4.7 -> libQtDesignerComponents.so.4.7.0
-rw-r--r-- 1 root root  2922856 2010-11-19 17:51 /usr/lib/libQtDesignerComponents.so.4.7.0
lrwxrwxrwx 1 root root       22 2010-12-11 17:21 /usr/lib/libQtDesigner.so.4 -> libQtDesigner.so.4.7.0
lrwxrwxrwx 1 root root       22 2010-12-11 17:21 /usr/lib/libQtDesigner.so.4.7 -> libQtDesigner.so.4.7.0
-rw-r--r-- 1 root root  6447360 2010-11-19 17:51 /usr/lib/libQtDesigner.so.4.7.0
lrwxrwxrwx 1 root root       17 2010-12-11 17:22 /usr/lib/libQtGui.so.4 -> libQtGui.so.4.7.0
lrwxrwxrwx 1 root root       17 2010-12-11 17:22 /usr/lib/libQtGui.so.4.7 -> libQtGui.so.4.7.0
-rw-r--r-- 1 root root 11425096 2010-11-19 17:51 /usr/lib/libQtGui.so.4.7.0
lrwxrwxrwx 1 root root       20 2010-12-11 17:34 /usr/lib/libQtOpenGL.so.4 -> libQtOpenGL.so.4.7.0
lrwxrwxrwx 1 root root       20 2010-12-11 17:34 /usr/lib/libQtOpenGL.so.4.7 -> libQtOpenGL.so.4.7.0
-rw-r--r-- 1 root root   941088 2010-11-19 17:51 /usr/lib/libQtOpenGL.so.4.7.0
lrwxrwxrwx 1 root root       20 2010-12-11 17:21 /usr/lib/libQtScript.so.4 -> libQtScript.so.4.7.0
lrwxrwxrwx 1 root root       20 2010-12-11 17:21 /usr/lib/libQtScript.so.4.7 -> libQtScript.so.4.7.0
-rw-r--r-- 1 root root  2688248 2010-11-19 17:51 /usr/lib/libQtScript.so.4.7.0
lrwxrwxrwx 1 root root       17 2010-12-11 17:21 /usr/lib/libQtSql.so.4 -> libQtSql.so.4.7.0
lrwxrwxrwx 1 root root       17 2010-12-11 17:21 /usr/lib/libQtSql.so.4.7 -> libQtSql.so.4.7.0
-rw-r--r-- 1 root root   261336 2010-11-19 17:51 /usr/lib/libQtSql.so.4.7.0
lrwxrwxrwx 1 root root       17 2010-12-11 17:34 /usr/lib/libQtSvg.so.4 -> libQtSvg.so.4.7.0
lrwxrwxrwx 1 root root       17 2010-12-11 17:34 /usr/lib/libQtSvg.so.4.7 -> libQtSvg.so.4.7.0
-rw-r--r-- 1 root root   373984 2010-11-19 17:51 /usr/lib/libQtSvg.so.4.7.0
lrwxrwxrwx 1 root root       18 2010-12-11 17:33 /usr/lib/libQtTest.so.4 -> libQtTest.so.4.7.0
lrwxrwxrwx 1 root root       18 2010-12-11 17:33 /usr/lib/libQtTest.so.4.7 -> libQtTest.so.4.7.0
-rw-r--r-- 1 root root   142712 2010-11-19 17:51 /usr/lib/libQtTest.so.4.7.0
lrwxrwxrwx 1 root root       17 2010-12-11 17:21 /usr/lib/libQtXml.so.4 -> libQtXml.so.4.7.0
lrwxrwxrwx 1 root root       17 2010-12-11 17:21 /usr/lib/libQtXml.so.4.7 -> libQtXml.so.4.7.0
-rw-r--r-- 1 root root   289704 2010-11-19 17:51 /usr/lib/libQtXml.so.4.7.0


Hope I will get better at Debian based Linux in time :).

Thank you for your help!

---

### Post by pytheas22 on 2010-12-11
Thanks for the output.  That gives me a better idea of what's where.  Please try this:

```
sudo mkdir /root/libQt
sudo mv /usr/lib/libQt* /root/libQt

```
After this, the command:
```

ls /usr/lib/libQt*
```

should return an empty directory listing.  If this is the case, try launching skype and let me know how it goes.

You shouldn't get an error message from 'mv' about being unable to find these files; if you do, that's weird and maybe there's something more complicated going on.

---

### Post by SnoopNL on 2010-12-11
Hello,

You were right getting the eror here.
After that tried purging skype.
Still same issue.

It happened after i installed aladdin token stuff.

Btw,

It now gives me the same error on my virtualbox.

This keeps getting more fun!

---

### Post by pytheas22 on 2010-12-11
> You were right getting the eror here.
After that tried purging skype.
Still same issue.

Sorry, I'm a little confused.  Do you mean the 'mv' command worked, or it gave you the same error as before?  Are there now any files whose names begin with libQt in your /usr/lib directory?

It's late here so I probably won't reply till tomorrow; hope this is not a pressing issue.

By the way, where did you install the aladdin etoken stuff from?  Did you download an installer from a website, install from the Ubuntu Software Center, or what?

It makes sense for VirtualBox to give the same error because it also depends on the libQt libraries for its interface.

---

### Post by masterchief101 on 2010-12-13
> **SnoopNL said:**
> Hello,

You were right getting the eror here.
After that tried purging skype.
Still same issue.

It happened after i installed aladdin token stuff.

Btw,

It now gives me the same error on my virtualbox.

This keeps getting more fun!

Try to uninstall "pkiclient" via apt or aptitude. Solved the problem for me.

libQtGui.so.4 => /usr/lib/eToken/libQtGui.so.4 (0xf6e9c000)
libQtCore.so.4 => /usr/lib/eToken/libQtCore.so.4 (0xf6be4000)
libQtXml.so.4 => /usr/lib/eToken/libQtXml.so.4 (0xf67cb000)
The pkiclient overwrites the normal libraries with the pkiclient ones. After uninstalling pkiclient everything should point to lib32 instead of lib/eToken again.

But if you rely on pkiclient then this solution is nothing for you. 

Offtopic: How did you manage to install your eToken properly. It didn't work on my System (Ubuntu 10.10 64 bit), so it was no problem for me to uninstall pkiclient ;) ) PM me on this topic.

Regards

---

### Post by paulysa1969 on 2011-03-29
Have similar type problem.

Cant start skype. When I start from command line
root@PaulSamsungNC10:/home/pauly# skype

I get:
skype: symbol lookup error: /usr/lib/libQtDBus.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

When I start VirtualBox from the command line
root@PaulSamsungNC10:/home/pauly# VirtualBox

I get
VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: /usr/lib/libQtOpenGL.so.4: undefined symbol: _ZN14QWidgetPrivate15checkWindowRoleEv

And also when I start QGIS from the command line

root@PaulSamsungNC10:/home/pauly# qgis

I get:
qgis: symbol lookup error: /usr/lib/libQtSvg.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

Thought it happened after I installed Google Earth 6 using these instructions:   [http://ubuntuforums.org/showthread.php?t=1666337](http://ubuntuforums.org/showthread.php?t=1666337)

Any suggestions would be appreciated :-(

Looks like all the libQt* files need replacing. Is there a way to put the original libQt* files back from the CD or a repository using sudo apt-get install or similar?

---

### Post by pytheas22 on 2011-03-29
**paulysa1969**: have you tried the instructions in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/115970")?  See in particular posts #25 and #41 (there are different solutions in each).  Based on the output you posted, your problem looks like the same one described on that page (and the last post indeed mentions Google Earth being the culprit).

---

### Post by Mojsije on 2011-04-01
hello, i can't seem to start skype too, it all worked few days ago and when i booted up again this morning, skype refused cooperation. i read everything here, tried some commands that were looking to refer to my problem.

i'm running lucid, and while starting skype all i get is:

skype: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

i tried reinstalling via skype website, via synaptic and still nothing.

also, i'm a bit ubuntu noob so have patience :)

---

### Post by pytheas22 on 2011-04-01
**Mojsije**: please try following the suggestions in post #21 and see if they get you anywhere.  If you're not sure what to do, let me know and I can provide more specific directions.

---

### Post by Mojsije on 2011-04-07
> **pytheas22 said:**
> **Mojsije**: please try following the suggestions in post #21 and see if they get you anywhere.  If you're not sure what to do, let me know and I can provide more specific directions.

hi, sorry for the delay i'm very busy atm, this is what i got so far:

when i try ti find libqtcore4 it doesn't give any locations, but when i try to install libqtcore4 it says that it's already installed.

when i go to the directories mentioned in #25 post of the bug report, libqtcore4 isn't there so i can't run dpkg.

please some more specific directions? :)

---

### Post by pytheas22 on 2011-04-08
> hi, sorry for the delay i'm very busy atm, this is what i got so far:

when i try ti find libqtcore4 it doesn't give any locations, but when i try to install libqtcore4 it says that it's already installed.

when i go to the directories mentioned in #25 post of the bug report, libqtcore4 isn't there so i can't run dpkg.

please some more specific directions? 

Where do you have libqtcore4 located?  In other words, what is the output of:
```

sudo updatedb #this command will give no output
locate -i libqtcore
```

I'm traveling till Wednesday, not necessarily with Internet access, but will do my best to respond as quickly as possible.

---

### Post by Mojsije on 2011-04-18
hi again :) sorry for another delay i was moving from my old office to the new one...

the output is:

```
123@123:~$ locate -i libqtcore
/usr/lib32/libQtCore.so
/usr/lib32/libQtCore.so.4
/usr/lib32/libQtCore.so.4.6
/usr/lib32/libQtCore.so.4.6.2
/usr/share/doc/libqtcore4
/usr/share/doc/libqtcore4/LGPL_EXCEPTION.txt
/usr/share/doc/libqtcore4/changelog.Debian.gz
/usr/share/doc/libqtcore4/changelog.gz
/usr/share/doc/libqtcore4/copyright
/usr/share/lintian/overrides/libqtcore4
/var/lib/dpkg/info/libqtcore4.list
/var/lib/dpkg/info/libqtcore4.md5sums
/var/lib/dpkg/info/libqtcore4.postinst
/var/lib/dpkg/info/libqtcore4.postrm
/var/lib/dpkg/info/libqtcore4.shlibs
/var/lib/dpkg/info/libqtcore4.symbols
```

---

### Post by pytheas22 on 2011-04-19
**Mojsije**: are you running a 64-bit system?  Because it seems strange that you have libQtCore.so only in your /usr/lib32 directory--normally I think it should be just in /usr/lib.  Perhaps you installed the 32-bit version of libQt for some reason.  If you let me know what your kernel architecture is (if you don't know, please just post the output of "uname -a"), that might provide the solution as to what's wrong.

---

