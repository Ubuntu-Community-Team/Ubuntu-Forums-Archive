---
title: "problem with eclipse"
date: 2006-04-25
forum: General Help
---

### Post by bakie on 2006-04-25
everytime i try to rune a program i get this weird error ](*,) 

** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...

ive tried to reinstall eclipse and all but nothing worked any1 got an idea about what the problem might be? i need to fix this very fast because i need eclipse for school

---

### Post by bugardifieno on 2006-05-20
Go to the Sun site and download their version of java and install it. The download is available at [https://sdlc2d.sun.com/ECom/EComActionServlet;jsessionid=FA17C6FBD8D17296076456FBB9CDAB7D](https://sdlc2d.sun.com/ECom/EComActionServlet;jsessionid=FA17C6FBD8D17296076456FBB9CDAB7D)

Download the self extracting file. Once you have it installed just click on your project in Eclipse and go "Project > Properties > Java Build Path. Remove the java library there. Then Add library > JRE system library > alternate jre  and browse to where sun java is installed. On my machine it is in /usr/java/j2sdk1.4.1_02/.  Once you have done that it should work fine. The basic Ubunutu java won't work apparently. 

I had the same problem but this fixed it.

---

