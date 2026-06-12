---
title: "Installing C compiler without CD or internet"
date: 2011-01-22
forum: General Help
---

### Post by rubber_band on 2011-01-22
I currently have Ubuntu 10.04, no installation CD, and no interwebs to connect my computer to.

What  I'm really looking for is some file (or set of files) to download that  will allow me to compile C programs (after moving said files onto a USB  and then move to and install on my compy at home).

Is this possible? How can one do this?

---

### Post by tredegar on 2011-01-22
You need to install the **build-essential** package, and its dependences.

This is going to be a PITA without an internet connection (missing dependancies).

So I suggest you beg or borrow one. You currently have one, or you would not be posting here. So just ask, get connected and do it.

---

### Post by dcottingham on 2011-01-22
This is certainly possible, though it might be a bit tedious. You want to start here:

[http://packages.ubuntu.com/lucid/gcc](http://packages.ubuntu.com/lucid/gcc)

Grab gcc, and the packages it depends on (you can decide if you really want the "suggests" ones), and then recursively grab the packages that those depend on. You can probably stop when you get to libraries (unless they have a "-dev" in the name) because they mostly come with the stock system.

You can then install them. If you forgot anything, it'll let you know, and you can go back and get it.

---

