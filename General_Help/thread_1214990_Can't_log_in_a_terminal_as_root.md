---
title: "Can't log in a terminal as root"
date: 2009-07-16
forum: General Help
---

### Post by w3sp4rm4l33 on 2009-07-16
Every time I try to log in the terminal as root, it keeps saying authentication failure. Though I am typing the password correctly, what is the problem?

[IMG]http://i25.tinypic.com/30s7fbp.png[/IMG]

---

### Post by michy99 on 2009-07-16
Try sudo -i

---

### Post by lykwydchykyn on 2009-07-16
root is disabled on ubuntu by default.  If you need a root prompt, do:

sudo -s

or 

sudo -i

---

### Post by coffeecat on 2009-07-16
You will find this useful:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by vinutux on 2009-07-16
you need setting su first

```
sudo passwd root
```

give password for sudo then give new password for root twice..

after that type su....

---

### Post by doas777 on 2009-07-16
just FYI, it is against the forum rules to post information on how to enable the root account.
expect a moderator shortly. [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
Aisyu explains the forum councils decision on this matter very nicely.

the only reason I know it's verboten, is cause I got yelled at for the same thing.

OP: seriously, in 2 years on ubuntu, I have never needed root beyond what sudo/gksu give me. it's a very elegant approach to balencing the problem of over-privileged users with accessibility and ease of use.

---

### Post by ramnarayan on 2009-07-16
try 
```
sudo su
```

it works

---

### Post by t4thfavor on 2009-07-16
I think its against the rules to tell people how to enable root on someone elses machine, I find it hard to believe that they would have a problem with enabling root on your own machine....

---

### Post by michy99 on 2009-07-16
[Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by running_rabbit07 on 2009-07-16
> **doas777 said:**
> just FYI, it is against the forum rules to post information on how to enable the root account.
expect a moderator shortly.

OP: seriously, in 2 years on ubuntu, I have never needed root beyond what sudo/gksu give me. it's a very elegant approach to balencing the problem of over-privileged users with accessibility and ease of use.

So give a person an OS but don't teach them how to use it? I had the same problem when I first started with Debian and had to reformat and install another OS because nobody was willing to help. At least direct people on how to access their permissions so that they can add root to their permissions through GUI. Then if they don't have administrative permissions they will be blocked already.

If it is a company system then it is the Admin's job to block the user from using terminal anyway, why would an employee need terminal unless he/she were an Admin doing maintenance?

I do realize you are just repeating what you have already been told but still gotta ask why cause I don't drink Bud Dry.

---

### Post by bodhi.zazen on 2009-07-16
Setting a root password is supported when required. We discourage instructing new users to set a root password without explaining how sudo works and the risks of setting a root password.

If you do not know the risks, you should not be handing out that advice, lol.

At any rate, IMO sudo -i is the preferred method with sudo su #2.

sudo -s preserves the user environment and cause problems (try sudo -s then "echo $HOME").

If you are a knowledgeable user and wish to run as root, you are free to do as you please on your system, but we ask you to plese share your experience with new users rather then posting "sudo passwd" or "gksu nautilus". Teach permissions and how to use sudo (it does have several advantages over su, lol).

---

### Post by doas777 on 2009-07-16
> **running_rabbit07 said:**
> So give a person an OS but don't teach them how to use it? I had the same problem when I first started with Debian and had to reformat and install another OS because nobody was willing to help. At least direct people on how to access their permissions so that they can add root to their permissions through GUI. Then if they don't have administrative permissions they will be blocked already.

ain't my rule man. I just gotta follow it since I like hangin out here, that's all. check out the link michy99 posted, or the edits I made to my post a min ago.

---

### Post by t4thfavor on 2009-07-16
Tutorials explaining how to enable the root account for a graphical login or autologin will not be supported on the forums and will be moved to the Jail.

This is CLI, and not autologin, so I don't see how it infracts the "law". Correct me if I am wrong.

However I do agree that sudo -i, and sudo su are better mothods by far.

---

### Post by bodhi.zazen on 2009-07-16
> **running_rabbit07 said:**
> So give a person an OS but don't teach them how to use it? I had the same problem when I first started with Debian and had to reformat and install another OS because nobody was willing to help. At least direct people on how to access their permissions so that they can add root to their permissions through GUI. Then if they don't have administrative permissions they will be blocked already.

Exactly, the point of this "rule" is to encourage teaching. "sudo passwd" without any further explanation is, in the opinion of the staff, a disservice to new users.

If you do not want to take the time to teach permissions or sudo, that is fine as well, move on to another thread that interests you, tons of people here who will teach.

---

### Post by bodhi.zazen on 2009-07-16
> **t4thfavor said:**
> Tutorials explaining how to enable the root account for a graphical login or autologin will not be supported on the forums and will be moved to the Jail.

This is CLI, and not autologin, so I don't see how it infracts the "law". Correct me if I am wrong.

That is correct.

 "Enforcement" of the policy varies, if there are a ton of threads where people post things like "sudo passwd" and "don't worry about learning permissions, just use gksu nautilus" and the staff feels it is detrimental to "proper teaching" of new users we may feel the need to act, it is a judgment call, and the point is to encourage teaching new users, not restrict what more knowledgeable users choose to do with their systems.

These are all tools and, like all tools, can be used and misused. We object when we feel they are misused.

---

### Post by running_rabbit07 on 2009-07-16
> **doas777 said:**
> ain't my rule man. I just gotta follow it since I like hangin out here, that's all. check out the link michy99 posted, or the edits I made to my post a min ago.

I wasn't trying to be mean but just today I recieved an this email,

"On Thu, May 21, 2009 at 02:15:57PM -0700, Ronnie wrote:[INDENT]> I have been trying everything I could to get to change my display  
> resolution. I have an NVIDIA chip set and have tried /aptitude install  
> nvidia-settings /and have had no luck with getting it to install. I have  
> tried different variances of that command but still nothing. This is  
> what I get when I try,
>[INDENT]>> ronnie@Ronnie:~$ aptitude install nvidia-settings
>> Reading package lists... Done
>> Building dependency tree       Reading state information... Done
>> Reading extended state information      Initializing package states... 
>> Done
>> Reading task descriptions... Done  E: Could not open lock file 
>> /var/lib/dpkg/lock - open (13 Permission denied)
>> E: Unable to lock the administration directory (*/var/lib/dpkg/*), are  
>> you root?
[/INDENT]> I am very new to Debian and Linux so I am not sure what else to try. I  
> am currently stuck with looking at a 800X600 screen and it's killing me.  
> I usually have the screen set at 1240X940 (or something close to that).  
> I would be very happy if you could help me with this.
[/INDENT]Only root can install packages.  Not regular users."

I just finally got a reply 2 months later for him to tell me I don't have root permissions on my own machine.(He didn't bother with advice to fix the problem with nvidia.) All he had to do was tell me I needed to set up a root account and of course in a more timely manner. Being that Ubuntu is built on Debian, I am technically still running Debian. If I had've been trying to fix my Ubuntu and recieved this kind of service, I would not have tried another Linux distro. I don't like to see people not get helped because that tells them they just need to fall back to Windows.

---

### Post by CatKiller on 2009-07-16
> **running_rabbit07 said:**
> All he had to do was tell me I needed to set up a root account

Had it been here, telling you to set up the root account would have been extreme overkill. An indication to use sudo, what it does and a link to the RootSudo wiki page would have been more than enough. And wouldn't have taken two months...

---

### Post by running_rabbit07 on 2009-07-16
> **CatKiller said:**
> Had it been here, telling you to set up the root account would have been extreme overkill. An indication to use sudo, what it does and a link to the RootSudo wiki page would have been more than enough. And wouldn't have taken two months...

True, that is one of the reasons I decided not to try Debian again because I am happy with being able to get help really fast in these forums. And, whenever possible, I try to help others with problems if I know how. Back then I had just finished A+ and had no clue about the commands in Linux. Of course my college doesn't even offer Linux+.

Though Ubuntu is Debian, Debian is not Ubuntu.

---

### Post by aysiu on 2009-07-16
Okay, well this thread's original question has been answered many times over.

The short story is ```
sudo -i
``` The long story can be found in the links to the wiki and to the forum policy on log-in-as-root tutorials.

---

