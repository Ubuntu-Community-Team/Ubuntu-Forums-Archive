---
title: "Checking to see if a directory exists remotely"
date: 2010-01-14
forum: General Help
---

### Post by TheFuzz4 on 2010-01-14
Hey Everyone,

So I'm working on my first bash script.  My script will do several things but right now I'm just trying to get the basic part of it down and working.
I have a section that looks like this

> #/!bin/bash
SERVER=$1

if [ ! -d `ssh ${1} /somedir`];then
	echo "Bad"
else
	echo "Good"
fi

The problem is that if you take that right now and run it, it will return back good in that it does exist.  What I need it to do is pass back that it's bad because it doesn't exist (that is unless you actually do have that directory in your root)  So if your a bash guru on this please feel free to jump in here and help me get this thing solved.  Thank you in advance for your assistance with this.

---

### Post by TheFuzz4 on 2010-01-15
Ok so through much trial and error I got this one figured out

if ssh server "[ -d /somedir ]";then
			echo "The directory exists so moving on"
		else
			echo "The directory was not found"
		fi

So if your stuck trying to put this into your script here ya go.

---

