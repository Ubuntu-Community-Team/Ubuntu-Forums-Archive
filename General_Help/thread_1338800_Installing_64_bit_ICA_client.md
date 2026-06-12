---
title: "Installing 64 bit ICA client"
date: 2009-11-26
forum: General Help
---

### Post by Grosneg on 2009-11-26
I have a clean install of Ubuntu 9.10 **amd64** on a Lenovo T61p. Runs beautifully except I can't get Citrix to run. When the wfcmgr command is run, the following error is displayed: ./wfcmgr: error while loading shared libraries: libXm.so.4: cannot open shared object file: No such file or directory. 
This is the output of ldd wfcmgr:
linux-gate.so.1 =>  (0xf77a3000)
	libXm.so.4 => not found
	libXp.so.6 => /usr/lib32/libXp.so.6 (0xf777f000)
	libXpm.so.4 => /usr/lib32/libXpm.so.4 (0xf776c000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7763000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7748000)
	libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf772f000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf772b000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7712000)
	libc.so.6 => /lib32/libc.so.6 (0xf75cd000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf757a000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf744b000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf743b000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7437000)
	libuuid.so.1 => /lib32/libuuid.so.1 (0xf7431000)
	/lib/ld-linux.so.2 (0xf77a4000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf7413000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf740e000)
Note the error: libXm.so.4 => not found
The solution on all the forums is to create a link to the lower version which I have done: ls -ls | grep libXm
0 lrwxrwxrwx  1 root root       23 2009-11-24 19:31 libXm.so.4 -> /usr/lib/libXm.so.3.0.2
Installed libmotif3 and latest 32 bit citrix client (maybe this is the problem?)
Can anyone assist?
Thanks

---

### Post by buspital on 2009-11-27
Just got this working myself. Linking to the lower version is the correct thing to do, but I think you're linking to the 64bit libmotif. 
Found a solution at [http://narnia.cs.ttu.edu/drupal/node/147](http://narnia.cs.ttu.edu/drupal/node/147). 
Go to [http://packages.ubuntu.com/jaunty/libmotif3](http://packages.ubuntu.com/jaunty/libmotif3) and download the 32 bit version of libmotif3, open it in archive manager and from the data.tar.gz archive get libXm.so.3.0.2 from usr/lib and copy it into /usr/lib32. Then, in /usr/lib32 create a link from libXm.so.4 to libXm.so.3.0.2 and you should be working

---

### Post by Grosneg on 2009-11-28
Thanks for the info buspital, however it is still not working. This is what I did. 
Downloaded libmotif3_2.2.3-4_i386.deb 
Extracted libXm.so.3.0.2 from the downloaded file and saved to /usr/bin32
Linked /usr/lib/libXm.so.4 to /usr/lib32/libXm.so.3.0.2. This is the ls -ls output:
0 lrwxrwxrwx  1 root root       25 2009-11-28 18:40 libXm.so.4 -> /usr/lib32/libXm.so.3.0.2
When running ./wfcmgr, this is the result: /usr/lib/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.4: cannot open shared object file: No such file or directory
Is there a need to change any file permissions?

---

### Post by buspital on 2009-11-30
> **Grosneg said:**
> 
Extracted libXm.so.3.0.2 from the downloaded file and saved to /usr/bin32


Do you really mean bin32? If so I'd guess that is the problem, it should be in lib32, I think, as that is where you are linking to.

Also, I didn't encounter any need to change permissions

---

### Post by Grosneg on 2009-12-01
Whoops, I meant to write "lib32" as that is actually where I saved it (bin32 doesn't exist). I'm no further ahead; anymore suggestions?
Thanks for taking time to help!

---

### Post by j0kerN on 2009-12-03
Make the link to libXm.so.4 in /usr/lib32/ instead of /usr/lib that worked for me.

---

### Post by buspital on 2009-12-03
> **j0kerN said:**
> Make the link to libXm.so.4 in /usr/lib32/ instead of /usr/lib that worked for me.

Yes, this seems right. Sorry, I didn't notice your libXm.so.4 was in /usr/lib

---

### Post by Grosneg on 2009-12-07
That did it, thanks J0kerN!
To reiterate for those trying to follow.
After installing the Citrix client (called receiver), download the 32 bit libmotif3 *.deb file from the links referenced above. You can't run this file as it is for the wrong architecture. You can however extract the file you need, save in the /usr/lib32 folder then link to it.
Downloaded libmotif3_2.2.3-4_i386.deb
Steps:
Extract libXm.so.3.0.2 from the downloaded file and saved to /usr/bin32 (instructions are above)
Link /usr/lib32/libXm.so.4 to /usr/lib32/libXm.so.3.0.2. (sudo ln -s /usr/lib32/libXm.so.3.0.2 /usr/lib32/libXm.so.4)
Run ldd /usr/lib/ICAClient/wfcmgr. You should get this output:
linux-gate.so.1 =>  (0xf77a8000)
	[COLOR="Red"]libXm.so.4 => /usr/lib32/libXm.so.4 (0xf7539000)[/COLOR]
	libXp.so.6 => /usr/lib32/libXp.so.6 (0xf7530000)
	libXpm.so.4 => /usr/lib32/libXpm.so.4 (0xf751d000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7514000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf74f9000)
	libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf74e0000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf74dc000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf74c3000)
	libc.so.6 => /lib32/libc.so.6 (0xf737e000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf732b000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf71fc000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf71ec000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf71e8000)
	libuuid.so.1 => /lib32/libuuid.so.1 (0xf71e2000)
	/lib/ld-linux.so.2 (0xf77a9000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf71c4000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf71bf000)
Note: I also found that Firefox did not know how to handle the .ica file and prompts for an action; ie, link to an application or save. Telling it to use /usr/lib/ICAClient/wfica and setting that file as the default fixed this issue.

---

### Post by tlroche on 2010-01-31
Trying to be a bit more clear and to finally eliminate Grosneg's typo about /usr/bin32, I created [this section of the CitrixICAClientHowTo]("https://help.ubuntu.com/community/CitrixICAClientHowTo#64-bit"). HTH.

---

