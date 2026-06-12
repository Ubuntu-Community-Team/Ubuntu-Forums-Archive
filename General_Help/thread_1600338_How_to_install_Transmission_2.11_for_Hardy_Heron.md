---
title: "How to install Transmission 2.11 for Hardy Heron?"
date: 2010-10-18
forum: General Help
---

### Post by kaunofrantas on 2010-10-18
Could someone post step by step instructions to install newest version of Transmission to Hardy Heron? 

By default it comes with 1.06. 

How do I install 2.11?

Thanks!

---

### Post by crichard on 2010-10-18
Try this PPA:

```
sudo add-apt-repository ppa:transmissionbt/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install transmission
```

---

### Post by kaunofrantas on 2010-10-18
when i try first command i get message:

> add-apt-repository: command not found

---

### Post by crichard on 2010-10-18
> **kaunofrantas said:**
> when i try first command i get message:

Sorry, It's my mistake. You are in Hardy, so you've to try a different method to add  PPA in your Sourcelist.

Kindly, follow the below commands,

```
gksudo gedit /etc/apt/sources.list
```

Enter your password

It'll open your sourcelist with root access.

Add the following lines,

```
deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu hardy main 
```
```
deb-src http://ppa.launchpad.net/transmissionbt/ppa/ubuntu hardy main 
```

Save and exit the file.

Now, we've to add PPA GPG key

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 365C5CA1
```

Update the source list

```
sudo apt-get update
```

To install transmission,

```
sudo apt-get install transmission
```

In-case if it's already installed, then upgrade using the following command,

```
sudo apt-get upgrade
```

Hope you get the new transmission in Hardy. :)

---

### Post by kaunofrantas on 2010-10-19
crichard,

You are the man. Thanks a lot. Worked like a charm!

---

