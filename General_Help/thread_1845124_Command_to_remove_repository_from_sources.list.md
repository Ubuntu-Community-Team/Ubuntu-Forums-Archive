---
title: "Command to remove repository from sources.list"
date: 2011-09-16
forum: General Help
---

### Post by overtone on 2011-09-16
Very simple question but i cant seem to find the command for it or enough documentation for me to figure it out. So on a side note some docs on repo lists or useful stuff would be appreciated.


Short version:

add-apt-repository ppa:sun-java-community-team/sun-java6

Is the command i used to add a repository. Whats the command to remove said repository?

'remove/release-apt-repository ppa:sun-java-community-team/sun-java6'?








Long version:

Basically the context is I'm trying to install and update sun-jre so i can play minecraft again. Seemed to work before the 1.8.


add-apt-repository ppa:sun-java-community-team/sun-java6
apt-get update
apt-get install sun-java6-jdk
update-java-alternatives -s java-6-sun

Figured this would work but it seems that the community java 6 ppa isnt live anymore. So the ppa was added fine but when I go to update i get the usual response of: 




W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/sun-java/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/sun-java/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found




A bit more investigation revealed that it had been moved to natty partners.

So now I'm trying to remove the ppa that i added but cant figure out how.
The command I used to add was 
'add-apt-repository ppa:sun-java-community-team/sun-java6'
I figured something like 
'remove/release-apt-repository ppa:sun-java-community-team/sun-java6'
would work. Any ideas?

********************************************
etc/apt/sources.list 

Is this where the ppas are added?

---

### Post by TeoBigusGeekus on 2011-09-16
```
gksu gedit /etc/apt/sources.list
```
Remove the offending line(s), save, exit.

---

### Post by haqking on 2011-09-16
> **overtone said:**
> Very simple question but i cant seem to find the command for it or enough documentation for me to figure it out. So on a side note some docs on repo lists or useful stuff would be appreciated.


Short version:

add-apt-repository ppa:sun-java-community-team/sun-java6

Is the command i used to add a repository. Whats the command to remove said repository?

'remove/release-apt-repository ppa:sun-java-community-team/sun-java6'?Long version:

Basically the context is I'm trying to install and update sun-jre so i can play minecraft again. Seemed to work before the 1.8.


add-apt-repository ppa:sun-java-community-team/sun-java6
apt-get update
apt-get install sun-java6-jdk
update-java-alternatives -s java-6-sun

Figured this would work but it seems that the community java 6 ppa isnt live anymore. So the ppa was added fine but when I go to update i get the usual response of: 




W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/sun-java/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/sun-java/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found




A bit more investigation revealed that it had been moved to natty partners.

So now I'm trying to remove the ppa that i added but cant figure out how.
The command I used to add was 
'add-apt-repository ppa:sun-java-community-team/sun-java6'
I figured something like 
'remove/release-apt-repository ppa:sun-java-community-team/sun-java6'
would work. Any ideas?

********************************************
etc/apt/sources.list 

Is this where the ppas are added?


use your update manager and choose settings and then in the various tabs  untick the one that corresponds to your PPA usually the other software  tab.

or you can :

```
gksudo gedit etc/apt/sources.list
```and then place a # at the front of the line you dont want it to use,  best to place a # there incase you want to use it again in the future,  the # comments the line out.

Easier to use the GUI though, and if you use gedit then make sure you use gksudo and not sudo.

cheers

---

### Post by Elfy on 2011-09-16
If you used add-apt then it' more than likely the repo is in /etc/apt/sources.list.d

```
ls /etc/apt/sources.list.d/
```

IF you can see it 

```
sudo rm /etc/apt/sources.list.d/nameofrepo.list
```

You can also do so from software sources in the software centre settings - look in the other software tab

Edit - you can also use the ppa purge 
[http://www.webupd8.org/2010/08/ppa-purge-added-to-official-ubuntu-1010.html](http://www.webupd8.org/2010/08/ppa-purge-added-to-official-ubuntu-1010.html)

---

### Post by overtone on 2011-09-16
lol. Software sources. So used to being in the mindset of trying to do everything in the console.

---

### Post by TeoBigusGeekus on 2011-09-16
> **overtone said:**
> lol. Software sources. So used to being in the mindset of trying to do everything in the console.

Of course you can, if you want to that is (it's the manly way anyway :lolflag:)
```
sudo nano /etc/apt/sources.list
```

---

### Post by Elfy on 2011-09-16
Which will still be of little help as all the ppa's I add get put in their own list in the sources.d folder :)

At least you said nano :p


```
ls /etc/apt/sources.list.d/
me-davidsansome-clementine-dev-natty.list
me-davidsansome-clementine-dev-natty.list.save
me-davidsansome-clementine-natty.list
me-davidsansome-clementine-natty.list.save
medibuntu.list
medibuntu.list.save
```

---

### Post by overtone on 2011-09-16
> **TeoBigusGeekus said:**
> ```
gksu gedit /etc/apt/sources.list
```
Remove the offending line(s), save, exit.

I actually tried this already. I couldn't find the lines that had anything to do with Java or sun.

---

### Post by Elfy on 2011-09-16
As I've said twice - look in /etc/apt/sources.list.d/

---

### Post by TeoBigusGeekus on 2011-09-16
Oops, sorry, I've forgotten me apt!
Ubuntu's getting trickier and trickier...

---

### Post by Elfy on 2011-09-16
:lol:

I'd forget where my head was if it wasn't bolted on

I can't remember when it changed tbh - I do though remember looking for things in sources.list and them missing

---

### Post by TeoBigusGeekus on 2011-09-16
> **forestpiskie said:**
> :lol:

I'd forget where my head was if it wasn't bolted on

I can't remember when it changed tbh - I do though remember looking for things in sources.list and them missing

Are you still using Fedora?
Cause in a year of sole Arch usage, I've forgotten almost everything Ubuntu...

---

### Post by Elfy on 2011-09-16
I've more or less gave up on it for a while - got eos (just sitting there being looked at from time to time) and xubuntu at the moment. What I really need to do is redo partitioning - too long a job for the moment :)

Will have another go shortly though - I got a tad fed up with fixing nvidia ...

---

### Post by TeoBigusGeekus on 2011-09-16
Damn!
Why don't they just sit around and develop some standards?
That's the biggest rant BSD users throw to Linux: every distro is another standard.

---

### Post by Elfy on 2011-09-16
Maddening isn't it :)

---

### Post by haqking on 2011-09-16
> **forestpiskie said:**
> Which will still be of little help as all the ppa's I add get put in their own list in the sources.d folder :)

At least you said nano :p
]


I agree on the nano or mostly i prefer vi/vim but i suggested that to a friend once for sources.list and he trashed the whole thing whilst trying to figure out how to use the editor ;-)

He screamed for notepad looking software, so i always refer people to gedit on here now

---

### Post by TeoBigusGeekus on 2011-09-16
> **forestpiskie said:**
> Maddening isn't it :)

It is...
I'd understand individuality if it offered something better for a distro, but the sources list?
It's a damn text file in every distro; is it too painful to have all of them give it the same name and location?

Some call it choice, that's what open source is about, etc.
I call it stupidity...

Anyway... [/rant]

---

### Post by Elfy on 2011-09-16
> **haqking said:**
> I agree on the nano or mostly i prefer vi/vim but i suggested that to a friend once for sources.list and he trashed the whole thing whilst trying to figure out how to use the editor ;-)

He screamed for notepad looking software, so i always refer people to gedit on here now

I tend to try for both if possible - in my opinion it's better to learn how to use a simple editor like nano when you;ve got a system that works than to try and use one in a recovery situation :)

If you know how to use nano when you boot to get something fixed - you've only got to remember one thing. I'm glad I did :lol:

---

### Post by Elfy on 2011-09-16
> **TeoBigusGeekus said:**
> ... :)

Anyway - I wonder what's happened to overtone - lost in space somewhere :(

---

### Post by nothingspecial on 2011-09-16
Impossible to keep threads on topic round here :rolleyes:

---

### Post by Elfy on 2011-09-16
It's not my fault - it's that hobgoblin guy

Edit - if teo and hacqing only had less than 50 beans I'd have had to look into bean harvesting accusations :p

---

### Post by TeoBigusGeekus on 2011-09-16
I have to justify my avatar... :biggrin:

---

### Post by nothingspecial on 2011-09-16
I would never suggest that it could possibly be you, far from it.
:P
Must be that hobgoblin guy.

---

### Post by TeoBigusGeekus on 2011-09-16
> **nothingspecial said:**
> I would never suggest that it could possibly be you, far from it.
:P
Must be that hobgoblin guy.

:-\"

---

### Post by haqking on 2011-09-16
> **forestpiskie said:**
> :)

Anyway - I wonder what's happened to overtone - lost in space somewhere :(


he is figuring out nano ;-)

---

### Post by Elfy on 2011-09-16
Must have rebooted to do it - but it's not too hard, nano -B /file/name and Ctrl+X is enough for what I do with it :)

Oh and Y or N ...

---

### Post by nothingspecial on 2011-09-16
> **forestpiskie said:**
> Must have rebooted to do it - but it's not too hard, nano -B /file/name and Ctrl+X is enough for what I do with it :)

Oh and Y or N ...

If haqings friend had used the -B option he wouldn't have screamed for something like notepad.

---

### Post by haqking on 2011-09-16
> **nothingspecial said:**
> If haqings friend had used the -B option he wouldn't have screamed for something like notepad.

he couldnt get figure out why pressing the ^ symbol and a letter typed it to the screen and didnt carry out the action ;-)

---

### Post by sikander3786 on 2011-09-16
Do I need to add something like....

Moved to Cafe :D

---

### Post by Elfy on 2011-09-16
Nope - I'm subscribed and I'll wait for the OP to return and then maybe move the offtopic stuff - though it is all good support dressed up in chat. 

If someone else comes along they'll learn 

ppa's install in their own lists in a seperate folder
apt changes 
nano has a backup option 
to read all posts :)
moderators are human too

:)

---

### Post by TeoBigusGeekus on 2011-09-16
> **forestpiskie said:**
> 
moderators are human too


Nice try...
Thread closed and enjoy your infraction!

---

### Post by Elfy on 2011-09-16
:)

---

### Post by Blackiwid on 2012-03-27
Is this thread still open, I think I did not found the right solution for that problem in the posts.

You only way told to make that happen was manualy with system tools liks nano.

The easy solution if you have installed the add-apt-repository (what was mentioned) is to just ust the same command and just add a -r or --remove before the target repo, and it removes it.

```
add-apt-repository -r ppa:xyz/123
```

hope that helps someone ;)

---

