---
title: "Living in a mobile home and how to set permissions to exist on a SD card?"
date: 2011-10-11
forum: General Help
---

### Post by ticktick on 2011-10-11
Hi there,
I am a very very happy (ubuntu) linux user and most of the time I use my desktop with a nice big screen. But sometimes, I need to travel with my Ubuntu notebook and the trouble always is to move my current work between the machines, because so many things have to be reconfigured to make everything work again.

I now put all my data on an SD card, and on both machines I do the following steps:
The SD card appears as media/mydisk. I create a link in my home directory
  $ cd /home/me/
  $ ln -s /media/mydisk
and so that my web pages and PHP scripts work in all browsers I also do:
  $ cd /var/www
  $ ln -s /media/mydisk
But the problem is that I don't seem to be able to get access with my local web servers.
When I try to go to say
  localhost/mydisk/somefile.html
then it tells me that I don't have the necessary permissions.

I then try to drop all access restrictions (this is probably acceptable, as I am offline most of the time) and call
  $ cd /media
  $ chmod -R 777 mydisk/
But that doesn't seem to help. I may have some wrong ideas about the concepts of symbolic links, permissions and the chmod command. Who can help me on that?

---

