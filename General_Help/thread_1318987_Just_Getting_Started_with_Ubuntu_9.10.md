---
title: "Just Getting Started with Ubuntu 9.10"
date: 2009-11-08
forum: General Help
---

### Post by oldefoxx on 2009-11-08
There are some things that I don't care for in Ubuntu 9.10, but give it enough time and enough complaints filed, and might get better over the next few years.

Most immediate thing is that I've decided that I am not totally happy with Evolution, the provided eMail client in Ubuntu.  There are a number of things that I don't really care for, such as that as soon as you send out email, it turns around and reads it back.  But what if you want to leave the email on the server after reading it, so that you can pull it down later on another PC?  It's either that or have a way to tell the email server to keep a copy of the email for downloading again later.  Another thing is that it seems geared to allowing only one user and one email account to be set up.  Don't know about you, but I have multiple email accounts I use and make reference to, as I want certain emails to come to me in a certain order or arrangement.

So I've decided to make a go with the Mozilla Thunderbird, which is from the same people that provide us with FireFox.  Getting Thunderbird is easy enough to do, but like many such files, comes to you in a compressed TAR file, and no real instructions on extracting the contents, where to put them, and the provided shell (.sh) file does not execute.  Leaves you sort of wondering what to do next.

By just trying, I found this simple way that works.  Open a Console Terminal window (look under Applications/Accessories/Terminal and click), then type in the following command:

    sudo apt-get install mozilla-thunderbird*

That should do it.  The installed program should now show up under Applications/Internet as Mozilla Thunderbird Mail/News.  That should get you started.  Oh, and Evolution is there as well, in case you want to give both of them a shot.

---

### Post by irishbreakfast on 2009-11-08
If you want an easy and safe route you can use the Ubuntu repositories.

Check out the Software Centre; Applications -> Ubuntu Software Centre

Or System -> Admin -> Synaptic Package Manager

Cheers

---

