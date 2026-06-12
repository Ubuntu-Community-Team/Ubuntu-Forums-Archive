---
title: "Embed webcam in Website"
date: 2012-05-23
forum: General Help
---

### Post by nw68868 on 2012-05-23
I am running Lubuntu 12.04  on my XBMC media center / Webserver.

I recently discovered that the "webcam-server" package is depreciated and that i dont have the dependancies to build it from source and that i cant get the dependancies to build it from source.

I found and started using "monitor" to serve a webcam. After some time with the configuration file i got it up and running and serving under port 8081. The problem is that i do not want it to serve to just anyone, more specifically i would like to embed it into a website on my webserver. That way i can have fancy text around it and use .htaccess to restrict access.

I know that i can configure via the configuration file monitor writing out video and picture snapshots but i have not figured out how to make them play friendly with a webserver. i dont want to just link to the latest snapshot, i want the same live video i can get from port 8081.


Help?

---

### Post by roelforg on 2012-05-23
So...
```

sudo apt-get build-dep webcam-server

```
didn't get you the build-dependencies?

---

### Post by nw68868 on 2012-05-23
webcam-server is no longer in the repositories.  When building from source I got 

```
~/temp/webcam_server-0.50$ ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... found
checking for working automake-1.4... missing
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc ) works... yes
checking whether the C compiler (gcc ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for a BSD compatible install... /usr/bin/install -c
checking for mawk... mawk
checking how to run the C preprocessor... gcc -E
checking whether gcc needs -traditional... no
checking whether ln -s works... yes
checking for ftime... yes
checking for inet_ntoa... yes
checking for malloc... yes
checking for memset... yes
checking for munmap... yes
checking for select... yes
checking for socket... yes
checking for strchr... yes
checking for strstr... yes
checking for unistd.h... yes
checking for getpagesize... yes
checking for working mmap... yes
checking for strftime... yes
checking for jpeglib.h... no
configure: error: Could not find jpeglib.h
``` 

so I installed libjpeg62 libjpeg62-dev
but the next configure I got

```
checking for jpeglib.h... yes
checking for linux/videodev.h... no
configure: error: Could not find linux/videodev.h
```

I googled the web and found:

"I think webcam-server needs to be updated to be compatible with videodev2.h, which is supplied with the current en future kernels. Videodev.h seems to be obsolete."

At this point I decided the motion package was my best bet.

---

### Post by nw68868 on 2012-05-23
I should mention I am running 12.04

---

### Post by roelforg on 2012-05-23
> **nw68868 said:**
> webcam-server is no longer in the repositories.  When building from source I got 

```
~/temp/webcam_server-0.50$ ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... found
checking for working automake-1.4... missing
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc ) works... yes
checking whether the C compiler (gcc ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for a BSD compatible install... /usr/bin/install -c
checking for mawk... mawk
checking how to run the C preprocessor... gcc -E
checking whether gcc needs -traditional... no
checking whether ln -s works... yes
checking for ftime... yes
checking for inet_ntoa... yes
checking for malloc... yes
checking for memset... yes
checking for munmap... yes
checking for select... yes
checking for socket... yes
checking for strchr... yes
checking for strstr... yes
checking for unistd.h... yes
checking for getpagesize... yes
checking for working mmap... yes
checking for strftime... yes
checking for jpeglib.h... no
configure: error: Could not find jpeglib.h
```so I installed libjpeg62 libjpeg62-dev
but the next configure I got

```
checking for jpeglib.h... yes
checking for linux/videodev.h... no
configure: error: Could not find linux/videodev.h
```I googled the web and found:

"I think webcam-server needs to be updated to be compatible with videodev2.h, which is supplied with the current en future kernels. Videodev.h seems to be obsolete."

At this point I decided the motion package was my best bet.

Obsolete doesn't mean broken.

Run this:
```

sudo apt-get install libv4l-dev

```
This'll install the missing header

---

### Post by nw68868 on 2012-05-23
> **roelforg said:**
> Obsolete doesn't mean broken.

Run this:
```

sudo apt-get install libv4l-dev

```
This'll install the missing header

I did, its already installed. I did a 

```
aptitude reinstall libv4l-dev
```

then tried recompiling. still got...

```
checking for unistd.h... yes
checking for getpagesize... yes
checking for working mmap... yes
checking for strftime... yes
checking for jpeglib.h... yes
checking for linux/videodev.h... no
configure: error: Could not find linux/videodev.h
root@Wall-E:/home/poptart/Make/webcam_server-0.50# 

```

What i'm looking for is a way to get video embeded in a website. It doesnt matter if it comes from Motion (which is up and working ) or from web-cam server.

---

### Post by nw68868 on 2012-05-25
Bump for help

---

### Post by nw68868 on 2012-05-27
soooo, i'm guessing this thread is dead because nobody knows how to embed video from the "motion" package into a website?

---

### Post by nw68868 on 2012-05-29
Getting closer!

I was searching through Motion's documentation and found this:  
[http://www.lavrsen.dk/foswiki/bin/view/Motion/WebcamServer]("http://www.lavrsen.dk/foswiki/bin/view/Motion/WebcamServer") 
which talks about a Java applet.

I know nothing of Java but I followed the directions here: 
[http://www.charliemouse.com/code/cambozola/]("http://www.charliemouse.com/code/cambozola/") 
I installed "ant" and "openjdk-6-jdk" along with all of their dependancies.

I build this SUPER simple website

```
<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>

<applet code=com.charliemouse.cambozola.Viewer
    archive=cambozola.jar width="640" height="480" style="border-width:1; border-color:gr$
    <param name=url value="http://192.168.0.101:8081">
</applet>


</body></html>


```

Now I have a box in the website,  but it says:
```
Security.AccessControlException: access denied (java.net.SocketPermission 192.168.0.101:8081 connect
``` and the rest of the message was cut off by the box.

So I 
```
root@Wall-E:/var/www/nathanweber# chmod 644 cambozola.jar

```

Still no joy!
How do I change permissions to make it play nice?

---

### Post by nw68868 on 2012-05-30
Bump for discouraged guy!!!!!!!

---

### Post by dagotron on 2012-06-03
I am still trying to find a solution myself.. I redirected the port 8081 to 80 with rinetd .. nothing.. 
I can view it all day long on the localhost machine with the applet and on port 8081, but I want to be able to view it through my web server. HELLLLP!!! LOL

---

### Post by nw68868 on 2012-06-04
So it turns out it was a java security problem.

Never using Java before i had no idea about permissions. This solved it!

```
# nano java.net.SocketPermission
```
in the java security folder. Then


```
grant {
  permission java.net.SocketPermission
        "localhost:port", 
	"connect, resolve";
};
```

---

### Post by nw68868 on 2012-06-04
> **nw68868 said:**
> So it turns out it was a java security problem.

Never using Java before i had no idea about permissions. This solved it!

```
# nano java.net.SocketPermission
```
in the java security folder. Then


```
grant {
  permission java.net.SocketPermission
        "localhost:port", 
	"connect, resolve";
};
```


I forgot you have to change the IP in the cambozola code that you insert into your HTML file. You MUST use the external IP

---

