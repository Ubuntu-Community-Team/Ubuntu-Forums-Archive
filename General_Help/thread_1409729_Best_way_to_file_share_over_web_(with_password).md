---
title: "Best way to file share over web (with password)"
date: 2010-02-17
forum: General Help
---

### Post by BevanFindlay on 2010-02-17
Hi,
I have set up an Ubuntu box at home as a server (though using the desktop version as I wanted a GUI - may at some point use it for plugging a TV into etc to play meda), but want to be able to remote access files on it when away from home.

I have set up with a DYNDNS account and know how to route web requests to the server machine, but want to know the best way to have it share files so that they are accessible (upload and download) via a web browser.  Ideally, it would run some sort of file manager-like interface, but as long as I can upload and download files, it doesn't matter if it is a bit rough. :)

I have a folder set up as a Samba share, and just want it to access that (and its subfolders).

The only other thing I would need from it would be that it requires a password before it lets someone do anything, as it will be open to the wild (while I probably won't use port 80, open is still open...)

Thanks!
  - Bevan.

---

### Post by Satoru-san on 2010-02-17
I&#12288;saw share, web, password, and Immediately thought of FTP.

I&#12288;use vsftpd it is really nice and small and will be very secure in sharing files. Make sure you jail the user to the home folder (chroot) and probably enable passv_permiscuious.

This way ANYONE including windows users can get your files. Make sure you use a random name/port for this user/server or you will have break in attempts (as you do with anything on the web) random port is the best idea.

Dont forget to open it in your router.

---

### Post by nixclusive on 2010-02-17
You might want to take a look at [operaunite](http://unite.opera.com/).

1. Install opera
2. make a unite account (one click dialog)
3. enable opera unite
4. enable file sharing application (html interface, password et al.)
5. install and enable the file inbox application from unite.opera.com
6. make sure your port 8840 is accessible from outside
7. you have a server at yourhostname.tld:8400

Though I don't find this highly reliable but might work out for you.

---

### Post by BevanFindlay on 2010-02-18
Satoru-san: thanks for the FTP suggestion - perhaps I was making things more complex than I needed to. :-)  The main place I need to access is from University, but I'm pretty sure I could do a (passive at least) FTP from there.

I might have a look at the Opera Unite thing, but probably only if I can't get things like FTP going.

Thanks :-)

---

### Post by BevanFindlay on 2010-02-18
Ok, getting there slowly on vsftpd, but wondering if rather than try and guess my way through the config file much more, if you might be able to tell me how to get it set up to do the following:

(1) FTP access is to only let users into /srv/samba/share/ (and subfolders), not anywhere else.  (Though I may want to change that location later).
(2) Users should have full access (read, write, create, delete files and folders) to above folder and subfolders.
(3) No anonymous logins.
(4) Probably only needs one user, though the normal login user I have on there is probably fine (except that I'm not totally keen on sending my server password in the clear...)  Am I best to set up a dedicated ftp user?  If so, what is the best way to do that?

I think that's probably all.  Having it let me use SSL would be neat, but only if it's not a pain to set up.

Thanks again :-)

---

