---
title: "Absolute noob needs help installing SMILE!"
date: 2010-03-18
forum: General Help
---

### Post by JoeLatics on 2010-03-18
Hi everyone, completely new to Ubuntu, I've been on Windows all my life, till their security failed me, and they wouldn't give me a new code to be able to use the software!

Anyway, I've been trying to install [SMILE](http://ubuntuforums.org/showthread.php?t=885201) onto my laptop, but I have no idea how to do it!

I copy and paste

sudo apt-get install libogg-dev libvorbis-dev libmad0-dev build-essential fakeroot checkinstall mplayer mencoder imagemagick

into my terminal, and it comes back saying "[sudo] password for joelatics".

It doesn't actually let me type anything back into it after that!

I'm at a complete loss, I know this will be dead obvious to you all, but I'm still getting used to not having a Start button at the bottom left!

Thanks for any help at all!

Cheers,
Joe

---

### Post by howefield on 2010-03-18
> **JoeLatics said:**
> it comes back saying "[sudo] password for joelatics".

It doesn't actually let me type anything back into it after that!


Are you entering your password ?

You won't see it being typed but it is, press enter once you have typed your password.

---

### Post by JoeLatics on 2010-03-18
> **howefield said:**
> Are you entering your password ?

You won't see it being typed but it is, press enter once you have typed your password.
Oh, wow, that worked!

Thanks a lot mate, it seems to be actually working now!

Getting used to this could take me a while! :p

Cheers again,
Joe

---

### Post by JoeLatics on 2010-03-18
Sorry, come across another problem:

What on earth does
"**Compile SOX in /usr with this command**...SMILE expects to see it in /usr and that's where this code puts it&#8212;execute one command at a time:

./configure --prefix=/usr 
make 
sudo make install"

mean?

I've got Sox (whatever the heck that is!) at /home/joelatics/Desktop/sox-14.0.1, what do I do?

Thanks again,
Joe

---

### Post by howefield on 2010-03-18
If it fails, you should get a clue in the terminal as to what went wrong. Paste it back here if you can't work it out.

Not an application I am familiar with, but I'll install it, see how it goes.

---

### Post by JoeLatics on 2010-03-18
> **howefield said:**
> If it fails, you should get a clue in the terminal as to what went wrong. Paste it back here if you can't work it out.

Not an application I am familiar with, but I'll install it, see how it goes.

Ah, right, I've just managed to do it (I think!)

Hopefully this will work, thanks a lot!

---

### Post by howefield on 2010-03-18
> **JoeLatics said:**
> what do I do?

You could try doing it the easy way, see if that works. :)

Using the getdeb repository - if you are using Karmic 9.10

Go to System > Administration > Software Sources > Third-Party Software tab, and add

deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb apps

To add the repository GPG key, copy/paste the following in terminal

wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -

Then still in terminal type

```
sudo apt-get update
```

then

```
sudo apt-get install smile
```

---

### Post by JoeLatics on 2010-03-18
Wow, that one worked!

Thanks a lot :D

I don't quite understand what I did there, though, for future installations, is there a guide on how to do this for other ones?

Thanks again!!!

Joe

---

### Post by howefield on 2010-03-18
> **JoeLatics said:**
> Wow, that one worked! Thanks a lot :D

You're welcome.

> I don't quite understand what I did there, though, for future installations, is there a guide on how to do this for other ones?

Normally you would want to stick to the Software contained within the Ubuntu repositories, easy to install and probably more "trusted".

If you have software you want to add that isn't in the repositories, look to see if they have a repository that you can add to your software sources list.

Last resort would be compiling, by last resort I only mean that as a new user of Ubuntu, it is certainly not the easiest way of getting software, but there might be occasions when it is all you have got.

Try a read at the Ubuntu Pocket Guide, you can download a free pdf from here.

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

It'll give you a good introduction to Ubuntu and take you well beyond that.

---

