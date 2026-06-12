---
title: "Weird Things Going On with the wirless notification."
date: 2011-06-11
forum: General Help
---

### Post by 3abdo3asal on 2011-06-11
Hey guys, I have a problem with the wirless notification thing it just disappers and disconnects from the internet making me have to log out and back in to reconnect to the internet every 2,3 hours after getting connected to the internet.
I have a zte mf 180 usb connect .
Here are images of it happening 
 [http://www.flickr.com/photos/63162479@N03/5822645760/]("http://www.flickr.com/photos/63162479@N03/5822645760/")
[http://www.flickr.com/photos/63162479@N03/5822078089/]("http://www.flickr.com/photos/63162479@N03/5822078089/")

---

### Post by linuxinstalledfromhdd on 2011-06-11
Would you like to try an alternative?

Wicd is a general-purpose network configuration server which aims
to provide a simple but flexible interface for connecting to networks.
Its features include a wide variety of settings.

 * ability to connect to (and maintain profiles for) both wired and
   wireless networks;
 * support for many encryption schemes, including WEP, WPA, WPA2 and
   custom schemes;
 * wireless-tools compatibility;
 * tray icon showing network activity and signal strength;
 * lack of GNOME dependencies (although it does require GTK+), making it
   easy to use in Xfce, Fluxbox, Openbox, Enlightenment, etc.

This is a metapackage, it allows installation of all the components of
Wicd, including one of the clients, which must be manually chosen.
```

sudo apt-get install wicd

```

---

