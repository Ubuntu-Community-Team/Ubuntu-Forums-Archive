---
title: "authentication failure for installing software or adding users"
date: 2010-05-24
forum: General Help
---

### Post by lucieperrie on 2010-05-24
Hi - 

I can login fine, and I can execute things from command line with sudo, and I have confirmed that I am a member of the admin group.

However when trying to install something from Ubuntu Software Center, or trying to add a user from GUI, I get an authentication failure. authlog just confirms there is an authentication failure but does not give any reason.

As background I happened to hose my permissions in the /etc/ folder recently. Had to much around to get sudoers working again. So not sure if I need to get all permissions correct to fix this problem, or what to do.

Thanks for any help.

- Lucy

---

### Post by mikewhatever on 2010-05-24
What exactly happened to the permissions of /etc?

---

### Post by lucieperrie on 2010-05-24
I was trying to fix a different problem a couple of weeks ago, and stupidly set all of /etc/ to chmod 777.

Then sudo didn't work and I had to set sudoers back to 440.

Then I started to realize that the 777 was a really bad idea so now have it all set to 755, but really have no idea how to get original permissions back short of reinstalling.

Not sure if this is what's causing the authentication problem but I'm not remembering anything else weird that happened that could have caused it.

BTW, since sudo at command line works fine and it seems like only gui apps have the authentication problem, I'm thinking it's something wrong with policykit getting the permissions???

But really I'm over my head here.

---

### Post by lucieperrie on 2010-05-24
This is what auth.log says when I try to add a user via the gui. (and the gui displays a shaky window that says "authentication failure" but never asks me for a password)

```

May 24 16:26:49 oiseau polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 FAILED to authenticate to gain authorization for action org.freedesktop.systemtoolsbackends.set for system-bus-name::1.54 [users-admin] (owned by unix-user:lucy)

```

---

### Post by mikewhatever on 2010-05-25
A quick look through *ls -l /etc* output shows that most of the files have permissions of rwxr-xr-x = 755, all root ownership, but quite a few have rw-r--r-- = 644, and some rw-r----.
I really don't know how to sort it out short of reinstalling.

---

### Post by seoseo on 2011-01-04
This is almost the exact same thing that has happened to me, and it started after allowed permission to an unstrusted site (I am not sure if this is the same as 'hosing my permissions'). The untrusted site in question was Facebook (the actual facebook, not a phish site) after I altered the DNS to access it. (it's blocked in the country I am living in).

Suffice to say I believe there must be a way around this outside of reinstalling.

*sighs*

---

### Post by chaosmos on 2011-02-22
hi everyone,

i am having exactly the same problem. i have recently played around with the permissions of /usr and had some issues with root privileges. i managed to change the permissions back and compared some permissions with another computer. they seem to be fine now, but ever since then i cannot access to software center and add a user from Administration/UsersandGroups. and i am getting the exact same message in /var/log/auth.log (I can install packages from synaptic package manager just fine and do everything from terminal without a problem.) 

has anyone figured out how to solve this problem yet :confused:

thanks!

---

### Post by quickstang38 on 2011-02-23
I'm also dealing with this issue. It seemed to start happening after trying to modify permissions for the icons folder. Although, now I can't remember what exactly I changed the permissions to.

Example of my problem:

Check for system updates, click install updates, Authentication Required box pops up without asking for password, click Authenticate and nothing happens.

The box stays there...

Any ideas?

---

### Post by joao.amaro on 2011-03-31
Hi All

I've the same problem. Solved it doing a ..

```
sudo chmod +s /usr/lib/policykit-1/polkit-agent-helper-1
```

---

### Post by Ghilteras on 2011-06-21
I've tried the chmod +s command but I still have the problem

auth.log shows:


Jun 21 11:45:25 angelo-desktop polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session9 FAILED to authenticate to gain authorization for action org.freedesktop.NetworkManager.settings.modify.system for system-bus-name::1.170 [<unknown>] (owned by unix-user:angelo)


I tried purging policykit and reinstall it to no avail

when I try to save a setting on the network manager a windows with the password input appears but it lasts less then a second then it disappear, I catched a screenshot of that windows and it looks like I failed to input the password (though I didnt even have the chance to write it)

any ideas?

---

### Post by YolandiB on 2012-01-17
This is the message I received - sounds like a problem.

An error occurred while checking for authorizations: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
You may report this as a bug.

---

### Post by dave373 on 2012-01-28
Hi,

I have just done a fresh install of Ocelot and I have the same issue.

I can 'sudo apt-get install' to get stuff, but the software center asks for a 'root' password, which fails as it is not set.

I will try to find a solution.... but if you know one.. please post it !!

Dave

---

### Post by cristobal.vio on 2012-02-10
same problem here
anyway the /usr/lib/policykit-1/polkit-agent-helper-1 file has the 'set user ID' bit already set

---

