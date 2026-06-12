---
title: "How do I install - MLT ver 0.7.6"
date: 2012-02-01
forum: General Help
---

### Post by Bushcraft Bill on 2012-02-01
I need this to get a program to work but have no idea on how to install this with the sudo apt-get MLT ver 0.7.6 does not work so how do I do it?
I have ubuntu 11.10 if that makes any difference...

---

### Post by llamabr on 2012-02-01
beats me.  What's mlt, what does it do, and where did you find it?

---

### Post by Bushcraft Bill on 2012-02-01
I just haver a program that wont run it wants this bit of program I need to find it is the problem and how to install it...

---

### Post by llamabr on 2012-02-04
> **Bushcraft Bill said:**
> I just haver a program that wont run it wants this bit of program I need to find it is the problem and how to install it...

What?

---

### Post by JonUK76 on 2012-02-04
It looks like it's something to do with video.  Quick bit of Googling found this PPA (Personal Package Archive) source - [https://launchpad.net/~sunab/+archive/kdenlive-release](https://launchpad.net/~sunab/+archive/kdenlive-release) which has the MLT 0.7.6 package in it.

You'd need to add the PPA to your software sources - there'll be instructions on the link about how to do this and how to install.

Through the terminal. I think it would be:

```
sudo add-apt-repository ppa:sunab/kdenlive-release
```

then

```
sudo apt-get install mlt
```

Not 100% but think that should work.  HTH

---

### Post by rojaasensei on 2012-02-04
> **Bushcraft Bill said:**
> I need this to get a program to work but have no idea on how to install this with the sudo apt-get MLT ver 0.7.6 does not work so how do I do it?
I have ubuntu 11.10 if that makes any difference...

If you are refering to "melt" it may be in this ppa:

[http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu](http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu)

---

### Post by jbgecko13 on 2012-02-05
> **rojaasensei said:**
> If you are refering to "melt" it may be in this ppa:

[http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu](http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu)

I have been working on this for a bit now because kdenlive has an MLT error stating to update it to 0.7.6 . I am running the update of a bunch of items to see if that fixes the problem, there was a melt update included.  if that does not work I will try the install mlt which sounds too easy :)

---

### Post by jbgecko13 on 2012-02-05
> **jbgecko13 said:**
> I have been working on this for a bit now because kdenlive has an MLT error stating to update it to 0.7.6 . I am running the update of a bunch of items to see if that fixes the problem, there was a melt update included.  if that does not work I will try the install mlt which sounds too easy :)


Running the latest update took me to version 0.7.7!!  and I spent about 2 hours on this yesterday.... oh well lesson learned!

---

