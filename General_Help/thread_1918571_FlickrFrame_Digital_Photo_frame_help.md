---
title: "FlickrFrame Digital Photo frame help"
date: 2012-02-01
forum: General Help
---

### Post by GSXRCarlos on 2012-02-01
Hi Guys, new to the forum and new to ubuntu & linux so please be nice ;)
 
I'm trying to follow this guide:
 
[http://www.flickrframe.com/laptop-picture-frames/ubuntu-picture-frame/](http://www.flickrframe.com/laptop-picture-frames/ubuntu-picture-frame/)
 
I'm using 11.10 and have got to this point 
 
> 
**Configuration and Flickr Authorization**
Create a directory for images for flickrframe and other local images(like the weather, news, etc…) do this as your flickrframe user, not under sudo.
Edit: The latest ubuntu comes with a Pictures directory in your home folder… I am using this to store ffimages for the time being so create an ffimages folder there… remember the sync piece wipes out anything that isn;t part of the current image set, so keep your ffimages directory as a subdirectory of your pictures folder.
*cd /home/flickrframe/Pictures*
*mkdir ffimages*
*mkdir rssimages *(for the weather and cnn scripts, if you choose to add them).
go to the web browser on some computer and type the ip address of the pictureframe computer…
*[http://xxx.xxx.xxx.xxx/authwizard.pl](http://xxx.xxx.xxx.xxx/authwizard.pl)*
Where xxx… is the ip address. or use [http://127.0.0.1/authwizard.pl](http://127.0.0.1/authwizard.pl)

 
and now i'm stuck - i cannot open authwizard.pl on my windows laptop (via tightvnc) or even directly as something useable, haveing read through authwizard.pl in gedit or as a text file it reads like a web page, but for some reason won't open up
 
Can anyone help?
 
Thanks

---

### Post by GSXRCarlos on 2012-02-05
ok, so i managed to sort it out
 
Had to change the permissions on a couple of other files
 
Has anyone else got a stora box (or any NASDUO) that they've tried to link to?

---

