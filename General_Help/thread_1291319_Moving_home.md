---
title: "Moving /home"
date: 2009-10-14
forum: General Help
---

### Post by magneze on 2009-10-14
I've recently created a new 10GB partition. Now I'd like to move all /home areas there in preparation for the upgrade to Karmic (I've heard that this is a good way of doing it).

How do I move /home to this new partition permenantly? :confused:

Cheerz

---

### Post by t0p on 2009-10-14
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Giblet5 on 2009-10-14
Let's assume that your new 10G /home partition is /dev/sdb2. Substitute your actual device for that value in the following:

```
sudo stop gdm
```

Log in on the text console.

```
cd /
sudo mv /home /home.old
sudo mkdir /home
sudo chmod 755 /home
sudo mount /dev/sdb2 /home
cd /home.old ##### MAKE SURE YOU ARE REALLY THERE BEFORE PROCEEDING!!!
sudo mv * /home
sudo start gdm
```

Now log in and we'll make this permanent.

```
sudo gedit /etc/fstab
```

Add an entry:

```
/dev/sdb2  /home           ext3    noatime         0       2
```

That should do everything, but you may wanna toss /home.old via ```
sudo rmdir /home.old
```

---

### Post by blur xc on 2009-10-14
> **Giblet5 said:**
> Let's assume that your new 10G /home partition is /dev/sdb2. Substitute your actual device for that value in the following:

```
sudo stop gdm
```Log in on the text console.

```
cd /
sudo mv /home /home.old
sudo mkdir /home
sudo chmod 755 /home
sudo mount /dev/sdb2 /home
cd /home.old ##### MAKE SURE YOU ARE REALLY THERE BEFORE PROCEEDING!!!
sudo mv * /home
sudo start gdm
```Now log in and we'll make this permanent.

```
sudo gedit /etc/fstab
```Add an entry:

```
/dev/sdb2  /home           ext3    noatime         0       2
```That should do everything, but you may wanna toss /home.old via ```
sudo rmdir /home.old
```

will sudo mv * /home preserve file ownership and permissions?  I did this recently, and when the chicken route- copying my home files over instead of moving them just in case.  I failed to use the -p option to preserve attributes, and all my home folders and files became the property of root:root.  Yeah- it was interesting trying to log in, let me tel you...

A few minutes in recover mode w/ some chown's in there fixed it.

BM

---

### Post by magneze on 2009-10-14
Thanks :)

---

### Post by Giblet5 on 2009-10-14
> **blur xc said:**
> will sudo mv * /home preserve file ownership and permissions?  I did this recently, and when the chicken route- copying my home files over instead of moving them just in case.  I failed to use the -p option to preserve attributes, and all my home folders and files became the property of root:root.  Yeah- it was interesting trying to log in, let me tel you...

A few minutes in recover mode w/ some chown's in there fixed it.

BM

Yes.

I'm not sure about file times though...

The best way to do the transfer is: ```
sudo bash
cd /home.old
tar cf - . | (cd /home ; tar xf -)
# verify accurate copy
cd /
rm -fr /home.old
exit
```

but some people here freak out at the "sudo bash" part...

---

### Post by magneze on 2009-10-14
> **t0p said:**
> [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)Hmmm, so I tried these steps and now can't boot into Ubuntu. I got the .dmrc permissions error, solved that now just get the mouse but no ubuntu desktop. Now booted into Windows for the first time in a while. :(

---

### Post by Giblet5 on 2009-10-14
> **magneze said:**
> Hmmm, so I tried these steps and now can't boot into Ubuntu. I got the .dmrc permissions error, solved that now just get the mouse but no ubuntu desktop. Now booted into Windows for the first time in a while. :(

Do you get the Ubuntu (Gnome) login screen?

---

### Post by magneze on 2009-10-14
> **Giblet5 said:**
> Do you get the Ubuntu (Gnome) login screen?No - I have autologin enabled.

---

### Post by magneze on 2009-10-14
Ok - I got it working with the steps from "What if it doesn't work?"

> chown -R *username:username* /home/*username*
chmod 644 /home/*username*/.dmrc
chmod 644 /home/*username*/.ICEauthority

I would suggest that these commands become part of the general instructions.

Bit worried for a while there, but seems ok now ..

---

### Post by blur xc on 2009-10-14
> **Giblet5 said:**
> Yes.

I'm not sure about file times though...

The best way to do the transfer is: ```
sudo bash
cd /home.old
tar cf - . | (cd /home ; tar xf -)
# verify accurate copy
cd /
rm -fr /home.old
exit
```but some people here freak out at the "sudo bash" part...

From the book "Beginning the Linux Command Line" they have this tar command for making an exact copy of a folder- 
```
tar -cC /old . | tar -xC /new
```
How does that differ from your use of tar to copy the files?

I'm a bit overwhelmed at times at the number ways there are to do the same thing at the command line.  I don't know how you can ever know which is the best way to do a thing.

BM

---

