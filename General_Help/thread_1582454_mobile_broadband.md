---
title: "mobile broadband"
date: 2010-09-26
forum: General Help
---

### Post by xVENUSx on 2010-09-26
I have mobile broadband which is T-Mobile UK.
The modem is a Huawei E160 and on a Ubuntu page, it says that this modem doesn't work at all.
That's the only internet source I have so I need to be able to use it.
I'm a newb to Ubuntu and tried to install usb_modeswitch and I'm going to test a different piece of software later.
My version of Ubuntu is 10.04.
Help me!

---

### Post by luvshines on 2010-09-26
See if helps
[http://ww.ubuntuforums.org/showthread.php?t=1473228&page=3](http://ww.ubuntuforums.org/showthread.php?t=1473228&page=3)

---

### Post by xVENUSx on 2010-09-26
I'm a newb so I don't know how to make the files and all that.
I need a easy solution.

---

### Post by muteXe on 2010-09-26
All you have to do is create a file according to that link! 
How easy do you want it? :)

---

### Post by luvshines on 2010-09-26
I think you can give comment #18 from the post a try.

1. Copy the line to be added <ctrl-c>

2. Open the file which is mentioned in any editor, say vi:
sudo vi <file-name>

3. Go to insert mode in vi [press i and bottom left should show INSERT]

4. Paste the line , as the post says in the end before the comments
[ctrl+shift+v] for paste

5. Exit insert mode [ Press Esc ]

6. Write and exit.[ :wq! and press enter ]

7. Reboot

---

### Post by cogier on 2010-09-26
I have posted this before but here it is again for you.

I have been very, very impressed with Sakis3G

What you need to do is run the following in Terminal and with any luck it will all fall into place: -

```
wget "http://www.sakis3g.org/versions/latest/i386/sakis3g.gz"
echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c
gunzip sakis3g.gz
chmod +x sakis3g
./sakis3g --interactive
```

It has worked for me on more than one computer with out a hitch.

More details here: - [http://www.sakis3g.org/](http://www.sakis3g.org/)

Have fun!!

---

### Post by gandaran on 2010-09-26
> **xVENUSx said:**
> I have mobile broadband which is T-Mobile UK.
The modem is a Huawei E160 and on a Ubuntu page, it says that this modem doesn't work at all.
That's the only internet source I have so I need to be able to use it.
I'm a newb to Ubuntu and tried to install usb_modeswitch and I'm going to test a different piece of software later.
My version of Ubuntu is 10.04.
Help me!
did you run the network manager mobile broadband setup wizard?

---

### Post by xVENUSx on 2010-09-26
I removed Ubuntu from my PC.
Took 5 mins so it's gone.

---

