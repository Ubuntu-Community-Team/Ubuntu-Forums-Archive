---
title: "User Environment Variable (PATH) HOWTO"
date: 2006-03-08
forum: General Help
---

### Post by Seinfeld on 2006-03-08
Hi..

Can you please help me how and where to set the PATH (user environment variables) ??

To be very clear here is the problem:

I do have a new software installed on my Ubuntu. It is the first time to be set for Linux after Solaris
Here is the path to opnet which I type on my command prompt to launch it
 ~$ /usr/opnet/11.5.A/sys/unix/bin/.
It successfully executes but does not work fully because the software requires to set the PATH environment variable. They only gave an example on the Cshell using setenv
I cannot really figure out how to set it on bsh
They did not explain how and where for bash. To my knowledge this PATH should be in .bashrc or bash_profile..  I am really stuck and mixed up with sissue

Can you please help where and what to do?? Can you please provide me an explanation about user environment variables in linux?? 

Thanks very much

---

### Post by taurus on 2006-03-08
Look in ~/.bashrc if you have one.  If not, create one like

```

nano ~/.bashrc
(Then, add the following lines...)
PATH=$PATH:/usr/opnet/11.5.A/sys/unix/bin/
export PATH
(Save it and exit...)

```

Then from a prompt, run

```

source ~/.bashrc

```

Now, /usr/opnet/11.5.A/sys/unix/bin/ is in your path and to make sure, run "set" at the prompt and you should see it in your path...

---

### Post by Seinfeld on 2006-03-08
Thanks taurus

Yes I do have .bashrc and .bash_profile

I just want to add a couple of things.. the OPNET software which is the one I am talking about launches by
 ~$ /usr/opnet/11.5.A/sys/unix/bin/opnet

"opnet" is the executable file, so shall we add it at the end or just leave it like till the directory /bin 

Anyways, I did what you told me exactly I got the following)

bash: lesspipe: command not found
bash: dircolors: command not found

yes set shows the path as follows

PATH=/usr:/opnet:/11.5.A:/sys:/unix:/bin:/.:/usr/opnet/11.5.A/sys/unix/bin/:/usr/opnet/11.5.A/sys/unix/bin/:/usr/opnet/11.5.A/sys/unix/bin/opnet:/usr/opnet/11.5.A/sys/unix/bin/.:/usr/opnet/11.5.A/sys/unix/bin/

( I am not root in all of the procedure, is it necessary ???)

when I try to launch opnet now. it does not.. here is what I get::

/usr/opnet/11.5.A/sys/unix/bin/opnet/dirname: Not a directory.
/usr/opnet/11.5.A/sys/unix/bin/opnet/basename: Not a directory.
/op_set_env: No such file or directory.


Did i do something wrong?? I really appreciate your help

Thanks a lot

---

### Post by Seinfeld on 2006-03-08
taurus

First of all SOLVED !!! \\:D/

Thanks a lot :p  

You being so knowledgeable made me greedy for some more knowledge ;)  I really appreciate your explanation if you can, Just for my interest..:-k 

Now, when I edited the file .bashrc as you told me.. I was a user. I ran 
```
source ~/.bashrc
```

But when i did the same as root, I got no errors when and all worked just fine, I am sure that .bashrc was edited and saved correctly as user though..

Now if I run set, I find  /usr/opnet/11.5.A/sys/unix/bin/ is in my path only as user and not as root.. Little confusing :rolleyes: 

The question is, should i always set my PATH and sun source ~./bashrc as root or user ??  and where should I run set to check >>?? or it does not matter ??

Can you please give me an explanation if you can.., what is exactly meant by PATH (User Environment Variables) and when usually we need to set them ? Thanks

Anyways......Thanks a  MILLION

---

### Post by taurus on 2006-03-08
Okay, I will do my best to see if I can explain this for you.  ;) 

Let's say that if you have a bunch of programs in /opt/data/bin/ and you want to run them from a terminal or what not and don't feel like typing the whole path, then you just need to add /opt/data/bin to your PATH.  Do not include names of the programs in your PATH or it will bomb you right now.  And since you only edit ~/.bashrc where ~ stands for your home directory, /home/Seinfeld (I think I've heard that name somewhere before :-k.  So ~/.bashrc = /home/Seinfeld/.bashrc), that why root doesn't know anything about the new path.  So, you can either add that new path to /root/.bashrc or you can also add that to /etc/profile for system wild.  

Then, "source ~/.bashrc" means rehash your ~/.bashrc again so everytime you've make a change to your ~/.bashrc, you either have to log out and back in again so bash will read in the new settings or just rehash it!  Why log out and back in again when you don't have to.  This is Ubuntu (Linux), not that crappy Windows.  

Hope I made sense since it's kind of late here and I need to get some sleep.    If you have any other questions, feel free to post or PM me if you wish.

---

### Post by thirdmusketeer on 2006-05-16
I wanted to change my shell to cshell, but it seems in my installation there is no cshell, how do I get cshell.

Thanks

---

### Post by Seinfeld on 2006-06-11
Hello thirdmusketeer

If I get your question right,, well...Just install it buddy.. 

```
apt-get update
```
```
 apt-get install csh
```

;)

---

