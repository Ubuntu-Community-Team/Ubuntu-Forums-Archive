---
title: "Plextor ConvertX help"
date: 2006-05-01
forum: General Help
---

### Post by Saist on 2006-05-01
okay, I'm using the latest Mepis Beta which is built from Ubuntu sources, and I'm hoping the two are close enough for some help here...

I'm trying to install Plextors ConvertX TV402U. The drivers have been released here : [http://oss.wischip.com/]("http://oss.wischip.com/") and the download is listed here: [http://oss.wischip.com/wis-go7007-linux-0.9.8.tar.bz2]("http://oss.wischip.com/wis-go7007-linux-0.9.8.tar.bz2")

The GO7007 driver, however, is not listed in either Debian(pure) or Ubuntu .deb sources, so I decided to download the tar file and follow the instructrions. Extracted the files to /home/saist/plextor, then used the terminal to go the top level file. 


Saist@5[wis-go7007-linux-0.9.8]$make

Your system appears to be missing fxload. Please install
fxload before continuing.

make: *** [fxload_check] Error 1


**used synaptic to get fxload from ubuntu servers*


Saist@5[wis-go7007-linux-0.9.8]$ make

***** Using kernel source in /lib/modules/2.6.15-21-386/build *****

make modules -C /lib/modules/2.6.15-21-386/build M=/home/Saist/plextor/wis-go700 7-linux-0.9.8/kernel
make: *** /lib/modules/2.6.15-21-386/build: No such file or directory. Stop.
make: *** [all] Error 2



****

okay... um. At this point I have absolutely no clue how to continue... What should I do from this point?

---

### Post by amjoconn on 2006-05-11
Reading the README file in the source directory (where you are typing make) has information you will need.

Specifically you need to install the kernel source (linux-source) for the kernel you are currently running, because the driver used it for when it builds.


Good luck,
Albert

---

### Post by mcglothi on 2006-06-27
I was having problems installing this as well.  I found this little bit on the mythtv wiki that helped a lot:

== Ubuntu 6.06 (Dapper)

Ubuntu no longer uses hotplug as of Dapper, to successfully build and install the Plextor drives issue the make install like: "make install USE_UDEV=y" 

See this site for more info and links:

[http://www.mythtv.org/wiki/index.php/Plextor_PX-TV402U]("http://www.mythtv.org/wiki/index.php/Plextor_PX-TV402U")

Hope this helps,

Tim

---

