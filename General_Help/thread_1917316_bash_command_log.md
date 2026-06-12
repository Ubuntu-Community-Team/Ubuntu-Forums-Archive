---
title: "bash command log"
date: 2012-01-29
forum: General Help
---

### Post by Valsteeg on 2012-01-29
Hey all, I'm very new to linux and shell scripting and have a question that i couldn't solve by myself:

When I run a bash script with several commands in it, are these commands logged anywhere on the system? Or does it only log the line I'm writing into the console?

My issue is:
I want to run a command that has a password in it and of course i don't want the password to be in the logs :)

I had the idea to fetch the password using curl (works well), but now I'm concerned about system logs. 

What I am trying to do is auto mounting TrueCrypt volumes and not having any information about them (keyfile, password) stored on the system. Storing keyfiles on a USB device is no solution, because i don't have physical access to the system.
I thought curl would do the trick, because i could easily remove all information from the webserver.

Using HTTPS to have communication secured would be the next step then.


Any help is greatly appreciated
Thanks!

---

### Post by cryptotheslow on 2012-01-29
Look at .bash_history in your home directory after you have executed your script. (note the leading dot)

So 

```
cat ~/.bash_history
```or

```
cat /home/Valsteeg/.bash_history
```By default that log file is set to be unreadable by other users. Which I presume you would also do with the script file containing the password. The up-shot being that if someone gained sufficient privilege to read your .bash_history they would likely be able to read the script itself - thereby defeating not having the password in the log!

Note - if you use sudo to execute the script the history may well get logged to root's .bash_history not your own. Also if you use sudo, the command will be logged to /var/log/auth.log so check there too if that is the case.

---

### Post by conradin on 2012-01-29
command 
```
h
```
shows you the history. You may pipe that to less to get a bit more manageable output 
```
h | less
```

---

### Post by Valsteeg on 2012-01-29
@conradin
Where would i put that command? I can't get it to work


@cryptotheslow
Thanks! That was pointing into the right direction!

The bash history file is one I already found, but that only got the commands in it, that I wrote to the console. So any command inside a script is not shown in that log.

But the var/log/auth has them in it, so I will have to find another way to do it or can i disable that logging feature?
I could overwrite that file after I have executed the script, right? But are there any other places containing this info?


And I'm not writing the password into the script. I thought I could just use curl inside my script to get the password over HTTP(S) like this:

bash <(curl -s [http://somedomain.com/secrets/bashcommands.txt](http://somedomain.com/secrets/bashcommands.txt))
(Will try it with HTTPS later on. Trying to keep it simple first...)

I tried it with the bashcommands.txt file containing 
echo Hello World!

And that worked, so I thought I could just load the commandline with the password in it using curl :)

Guess it is a really pathetic way to do this, but heck, I have no clue how i could do it the right way....

---

### Post by JKyleOKC on 2012-01-29
If you're concerned about security, you definitely want to leave the /var/log/auth.log file alone! It's one of the main forensic tools you've got, to determine if an intruder has attempted to gain access to the system.

The password is never written to that file. The "PWD=" entries you see there are the "Print Working Directory" result for the logged command, not a PassWorD entry (I've used caps to emphasis the abbreviations in both cases).

So far as I know, the only time any part of a script is logged is if the script itself requests this action. The most risky part of your procedure is having the password in the script itself, because anyone who gains read access to the script can see it. A first step toward blocking this security hole is to make the script inaccessible to everyone other than yourself, or preferably to a hidden user account to which only you have access or even know of its existence...

EDIT: I may have misread your initial message; are you saying that each command within the script is logged to the auth.log file? My experience is that only requests for changes in authentication level are logged there; i.e., using sudo, logging in, or using the graphic authentication tools. Also are you actually putting clear-text passwords into the script file itself? Many programs allow you to store credentials in separate files, and refer to those files in the command that launches the program. This would store the passwords in a system somewhere, but you might be able to obfuscate things enough to make it work by storing them on your own machine and having the remote system call back to obtain them.

Any dealings with a remote system, though, are always subject to MITM (Man In The Middle) attacks, which can be almost undetectable...

---

### Post by Valsteeg on 2012-01-29
Yeah you are right. Messing with the logs wouldn't be that a good idea. Hmmm.
So then my whole attempt doing it this way failed.

Even though this gets offtopic now, but how would you solve my problem?

I have a server with a system drive and 2 encrypted drives that I want to automount with TrueCrypt when the server is turned on.
I don't want to store any information needed to decrypt the drives on the system and i want to be able to turn off this automount feature just in case I don't have access to the server anymore, for whatever reason...

So I think I need a second system that somehow controls this automount. But how can this be done?
Do you have any ideas what i could search for to get this working?


EDIT:
Yeah sorry, I am no native speaker and it is kinda hard for me to express myself regarding technical topics :/

Well what i found in the logs was a 

COMMAND=/sbin/hdparm -i /dev/sdb

what was a command I used in one of my scripts. That's why I think all commands are logged. Not only the commands I type into the console.
"Man in the middle" is a security risk, but shouldn't be that a big deal once I use secured channels like HTTPS. At least I think that gives me enough protection.

EDIT2:
Yes i was using sudo and I think for mounting I would have to use sudo as well....

EDIT3:
"Many programs allow you to store credentials in separate files, and refer to those files in the command that launches the program. "

Right, TrueCrypt allows the usage of keyfiles, but I just read an article about some weakness in the keyfile algorithms. The conclusion of the article was: use passwords and no keyfiles with TrueCrypt.
I don't have that article in English, otherwise I would share it.

---

