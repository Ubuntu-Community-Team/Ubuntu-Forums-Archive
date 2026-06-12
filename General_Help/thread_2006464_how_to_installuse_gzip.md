---
title: "how to install/use gzip?"
date: 2012-06-19
forum: General Help
---

### Post by Jacob72 on 2012-06-19
How do you install the gzip compression tool on 11.10? Does it appear as an app like winzip, how do you  use it? Can you only compress files via the Terminal, I am not skilled at this.

Thanks

---

### Post by Lars Noodén on 2012-06-19
For me it is easiest to work in the terminal, look in the manual page ([font=Courier New]man gzip[/font]) for the details.

But if you want a graphical interface, then nautilus can work with gzipped files.  Just open nautilus and then click on the compressed file.  Nautilus will then show you what's in it.

---

### Post by Jacob72 on 2012-06-19
Thanks, learning to use the Terminal seems to be a big learning curve that I hope to do over time.

I am working on LAMP and trying to speed up a website by compressing js files. I was able to gzip my js file using the terminal from watching this[ yt tutorial]("http://www.youtube.com/watch?v=soHa5LiftHQ"). But now the js file shows file permissions -rw-rw-r-- and is no longer working on my local web page? Do I Need to change to -rw-rw-rw- and how? 

Do I need to activate LAMP to accept gzip files?

---

### Post by Lars Noodén on 2012-06-19
Don't set the files to -rw-rw-rw-, that would be very insecure.  

What you might be looking for with Apache2 is the [mod_deflate](https://httpd.apache.org/docs/2.2/mod/mod_deflate.html) module.  It will compress outgoing files for you and cache them.

Here is a brief HowTo on mod_deflate:
[http://www.howtoforge.com/apache2_mod_deflate](http://www.howtoforge.com/apache2_mod_deflate)

---

### Post by Jacob72 on 2012-06-19
The other js files in the directory are set to -rw-rw-rw- , I did not set them, they are part of jquery apps?

---

### Post by Jacob72 on 2012-06-19
> What you might be looking for with Apache2 is the [mod_deflate]("https://httpd.apache.org/docs/2.2/mod/mod_deflate.html") module.  It will compress outgoing files for you and cache them.

Here is a brief HowTo on mod_deflate:
[http://www.howtoforge.com/apache2_mod_deflate](http://www.howtoforge.com/apache2_mod_deflate)

Does this enable the use of gzip or is mod_deflate it's own compressor?

---

### Post by Jacob72 on 2012-06-19
Is mod_deflate an option that web host companies provide? Or is it something you apply to files locally and then upload to your remote host? Sorry bit confused, I am only testing locally, I am not hosting any live sites  :-?

---

