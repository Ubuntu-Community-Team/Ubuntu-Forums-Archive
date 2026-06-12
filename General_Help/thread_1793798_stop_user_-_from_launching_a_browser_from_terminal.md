---
title: "stop user - from launching a browser from terminal."
date: 2011-06-30
forum: General Help
---

### Post by Jordy_224 on 2011-06-30
Ubuntu_forum,

How do I stop a user, from gaining access to the internet(port) via a **restricted browser**? In other words, I want a general user to only to have access to Firefox and no other browsers. 

My first approach so far, has been to write a bash shell script. It terminates a program based on keywords from known browsers (opera, asus, ect). 

any alternative solutions?

-jordy

---

### Post by pub_tsop2011 on 2011-06-30
I thought there was a program on the repository that could do this....?

---

### Post by cybergalvez on 2011-06-30
> **Jordy_224 said:**
> Ubuntu_forum,

How do I stop a user, from gaining access to the internet(port) via a **restricted browser**? In other words, I want a general user to only to have access to Firefox and no other browsers. 

My first approach so far, has been to write a bash shell script. It terminates a program bases on keywords from known browsers (opera, asus, ect). 

any alternative solutions?

-jordy

Can't you just not have them installed? if your users can't install programs (which should be easy to restrict) and if FF is the only browser won't that do what you want? 

I know users can install software locally to their own account without root access, but if they know how to do that I don't think your shell script is going to stop them

---

### Post by WorMzy on 2011-06-30
Remove the executable bit for others from the executable.

```
sudo chmod o-x /path/to/executable
```

If you want specific users to be able to use the application, add them to a group, and change the group ownership of the executable to the new group.

```
sudo chgrp groupname /path/to/executable
```

---

### Post by hawthornso23 on 2011-06-30
A permissions based approach might be another way to do it. 

For example you could set up a special user called 'net' and tell firefox to always run as user `net'. Give user 'net' permission to connect to the internet and deny it to all other users. Denying internet access to a specific user is a much more common problem. There might be some undesirable side effects - everyone might end up with the same profile - so maybe you might have to have a separate netuser for each user. But it looks to me like a feasible alternative approach to the problem.

Good Luck.

---

### Post by pub_tsop2011 on 2011-07-01
Doesn't creating a user account ignor the problem that any user can download a browser and run it from the desktop....I think that the main issue.  
 

 It maybe better to run a cronjob that stops certain browsers.

---

### Post by Habitual on 2011-07-01
How about "talking" to the user? You do remember talking, yes? :)

---

### Post by pub_tsop2011 on 2011-07-01
There is a program called KUser that manages a user permissions. Perhaps you can use that along with hawthornso23 suggestion. I think its an interesting question and worth posting a solution...

---

### Post by sandman887 on 2011-07-02
> **pub_tsop2011 said:**
> Doesn't creating a user account ignor the problem that any user can download a browser and run it from the desktop....I think that the main issue.  
 

 It maybe better to run a cronjob that stops certain browsers.

How often would you have it run? Users could install a browser and use it for a certain amount of time until the cron job ran again, right? I guess it would depend on what the job did.

---

### Post by Jordy_224 on 2011-07-03
@WorMzy

Yes, the goal is to stop user from downloading and launching a browser from the terminal. The browser is compromising security. So I want to block internet access to all download browsers

So far I am attempting to change the group policies... 
hopefully there is a linux manual with a guide on how to do this.

---

### Post by mikejonesey on 2011-07-03
many ways to do this a few already mentioned, how abouts moving the std display address and setting the sys env var DIPLAY to null for those users, (no gui apps...),if u just want for browsers does that include wget? or just internet browsers... maybee if its all web you just want to block port 80 outgoin requests... (can be done verry easily with iptables...)

...in short you need to decide what you are going to block, a category of software ie browsers wont work becase you can get imposters... blocking permisions, ports, protocals or guis can work depending on what you decide you want :) hope this helps...

---

### Post by SeijiSensei on 2011-07-03
> **Jordy_224 said:**
> Yes, the goal is to stop user from downloading and launching a browser from the terminal. The browser is compromising security. So I want to block internet access to all download browsers

Which browser is it, and how is it "compromising security?"  Inquiring minds want to know.  I'm having trouble understanding how a particular browser could somehow undermine the security of a Linux workstation, especially if the user doesn't have root privileges.

I think this is a fruitless endeavor myself.  You going to block elinks?  How about wget?  What about telnetting to the web server's port 80 and entering HTTP commands?

---

### Post by pub_tsop2011 on 2011-07-03
@[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") Not a very good way to think of a linux challenge....it should be done just for the sake of understanding more about linux.  Why write that you don't think its important?  
 
Actually, it is an valuable question.  
 
In general, he is asking this. How do I allow limit** one** application from a** program **type  
  This is the same as saying I want only all users to use openoffice and not abiword. Tomboy notes and not wikinotes. Better applications over "crappy" applications.  
 
I can see how this could be important, especially if there is a security issue with a software. Who wants someone running a sneaky program by terminal privileges.

---

### Post by SeijiSensei on 2011-07-03
Well if you want to limit your users to a specific set of applications, just remove the ones you don't want them to have.  That's not what he's trying to accomplish, though.  He apparently wants to prohibit a user from downloading and installing any other browser besides the already-installed Firefox.  Users without root privileges can still download a binary tarball of a browser, unpack it in their home directories, and run it from there.  I do that from time to time to test Firefox releases that haven't yet appeared in the repositories.  If you give me the ability to download files, you've pretty much guaranteed that I can install a private browser.  Plus, if I know that you're trying to keep me from doing this, I'm going to rename the browser binary to something obscure so any monitoring programs won't notice it.

The primary line of defense remains the distinction between users with root privileges and ones without them.  An ordinary user can't write to the system areas like /usr or /etc where real damage could occur.  Remember that Unix was designed from the ground up to support multiple users and enforce security among them.  Any capable programmer could write a low-level C program that could have disastrous consequences if run with root privileges, but without those privileges the program has no teeth.  On the other hand, I could write a trojan program that ordinary users might run that could do unpleasant things like join a botnet.  Protecting against those types of threats usually requires some additional armament at the router.  For instance, routinely blocking traffic between a workstation's "high" ports (1024-65535) and high ports on remote machines can help.

I'm still trying to understand why the OP thinks other browsers are somehow security risks.  Why is Firefox safer than rekonq?  My main difference of opinion concerns the original premise of the request, not so much the question of implementation.

There may be ways to use AppArmor or SELinux to accomplish what the OP desires.  I've never delved into either of them very deeply so I defer to others' opinions.

---

### Post by Jordy_224 on 2011-07-22
@mikejonesey

Thanks for the tip. 
If I set the environmental **DISPLAY** variable to **null**, the graphical display manager will not load. My goal is to disallow GUI applications from being run in the terminal only.

```
printenv DISPLAY
export DISPLAY=
```

**result :** after login graphical windows interface doesn't load and the screen returns to the login prompt. 


I'm in the process of learning terminology so I apologize in advance, but I know that ssh xterm allows you to run GUI apps. on a remote machine, so I hoping to learn about the process and disable this feature on a local machine....

> .in short you need to decide what you are going to block, a category of software ie browsers wont work becase you can get imposters... blocking permisions, ports, protocals or guis can work depending on what you decide you want hope this helps...

Its just that. blocking guis, or in this case all guis run by terminal for starters. I assume there is an environmental variable that I can adjust.

---

### Post by pub_tsop2011 on 2011-07-22
Yeah, people have inquired about this as problem but in different ways. 
its called an **outgoing firewall.**  Unfortunately, there isn't an application for linux, so you can adjust the IP tables.

Jordy, as you expect, may of these forum topics are **littered** with people saying linux is 100% secure and not needed. But I suggest you check into it anyway. 

[PHP]http://ubuntuforums.org/showthread.php?t=335659
[/PHP]

[PHP]https://help.ubuntu.com/community/IptablesHowTo[/PHP]

Hope this helps, sadly many people will post on a board but never post a link to help explore the problem or where you can learn how to do it.  A big problem in forums IMO.

---

### Post by Jordy_224 on 2011-07-22
thanks Im checking out iptables

---

### Post by Jordy_224 on 2011-07-26
_**SOLVED**_::::  I found alternate **solution** to the problem. The problem is that a user is gaining access to the internet using a restricted browser. The browser is a potential compromise to security. I want everyone to use firefox. 

Given that all browsers run by the command line go through port 8080 Http-alt. I created a rule that blocked input to the port in the iptables. By restricting the port I am able to prevent the user from not only running restricted browsers but also other Internet programs. Which is the best case scenario , rather then blocking the application. 

```

iptables -A INPUT -j DROP -p tcp --destination-port 8080 
```

thanks for you help, 

-Jordy

---

### Post by scruffyeagle on 2011-08-29
Interesting discussion here. I have a tuppence to contribute.

If there's a worry about Users downloading binaries, unpacking them, and installing them, open the "Users and Groups" utility. Under "Groups", find the group "sudo". Uncheck the User names of everyone you don't want having the capability of installing software. I don't know if this will stop them from unpacking & running software from directories in their own profile, but it would prevent anyone from being able to install software on a system-wide basis. The only people who could update software, download from repositories, or run commands w/ root privileges after you've done that, would be whoever had been left checkmarked within the "sudo" group.

---

