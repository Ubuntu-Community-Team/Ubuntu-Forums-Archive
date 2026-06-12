---
title: "Send commands from one Terminal to another"
date: 2011-01-30
forum: General Help
---

### Post by W@@dy on 2011-01-30
Hi, sorry for the weird title and I'm sorry if this is the wrong area.
1) I'm new
2) I'm relatively new to Linux/Ubuntu
3) I don't really know how to classify my question, so I just went with general


Okay, so I'm running a server on my laptop which is running the latest Ubuntu. It's a Minecraft server, nothing fancy (laugh it up).

No problems whatsover. I start the server using the a command, which I recently saved as a bash file.

Now when the server starts a ton of text flies through the terminal, and at the end, I can enter in my own commands for the server.
Ie. "save-all" saves the map, "stop" stops the server.

Now, I'd like to be able to control my server remotely. I have already set up an ssh server on the laptop, and I've connected to it successfully.

[SIZE=2]*My question*[/SIZE]
[SIZE=1][SIZE=2]Is it possible for me the view the server logs remotely (I'm using puTTY)?

When I connect, it's essentially like opening a separate terminal window. So I can't tell my server to "stop" or "save-all"

How can I get send those commands to my server? I tried the bash command to start the server just because I figured I should try *something* before I ask around. Yeah it didn't work lol.

Am I out of luck? Or is there really some way to do this?
[/SIZE] [/SIZE]

---

### Post by Habitual on 2011-01-30
**This Absolutely CAN BE DONE!** and it's a great Q btw.
And good for you for trying "something" before asking this question.
+1

1st from your Local machine:

```
ssh-keygen -t rsa ( (leave passphrase empty)
```
Next you are copying the key you just made to the remote server...
```
scp ~/.ssh/id_rsa.pub  user@domain.com:/home/$user/.ssh
```

On the Remote system:

```
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
``` 
then exit/logoff/quit from the remote system.

Remote command from your Local Machine:
Reboot from "here"...
```
ssh -t user@domain.com reboot
```

Substitute reboot for your commands.

Here's some real-life examples of remote commands from a local machine:
ssh -qt [email]user@domain.com[/email] 'bin/dump.sh'
ssh -qt [email]user@domain.com[/email] 'whereis bash'
ssh -qt [email]user@domain.com[/email] '/path/to/save-all' <-- this is your stated command.
ssh -qt [email]user@domain.com[/email] 'less /path/to/log/file'

-q suppresses the "Connection to domain.com closed." message(s).


You get the idea?

I am subscribed to this thread, so feel free to ask me for help.

Good luck.

---

### Post by W@@dy on 2011-01-31
Whoah.

Lol went right over my head first time I read it.

Okay my first confusion is terminology between local and remote.

Let's pretend I'm away at college.
In that case, my laptop with the server would be the remote computer, and the computer in the school library is the local computer. Correct?

When I first read it I had it reversed. Second time through, I switched it and it seemed to make a bit more sense.

First Step:  I'm generating a key. Simple enough.

Second Step: This line copies the generated key to my laptop back home. So I'd enter this into puTTY, right?

Third Step: Log on to my remote system through puTTY (if I didn't do that in step 2) and enter that line in. My best guess is that it's authorizing the key.

Fourth Step: Disconnect

(this is where I'm a little lost)

Fifth Step: Now I reconnect? I think I understand what's going on. It seems like your telling the local pc to reboot to the remote...system...um...lost the thought. lol
It's not an actual "reboot" is it? I can't imagine it would be.
It's just a way of sending your command in. Somehow. Or something.
[/noob interpretation]

Well I'll definitely try this out. Tomorrow I'm actually going into college and they have puTTY.
I can follow the steps you gave me, I just don't completely understand what's happening.

I'll learn :D seems simple enough provided I can remember the commands at some point.

Which leaves me rather speechless regarding how you know them off hand >.>

---

### Post by Habitual on 2011-01-31
Fair enough.

Terminology:

**Local** Computer can be any computer you happen to be sitting at.
**Remote** Computer is any computer you are accessing or connecting **to**.

"my laptop with the server would be the remote computer, and the computer in the school library is the local computer. Correct?"
If your laptop IS the server and you are IN the school library, then yes.

If you travel to Mom's house for the holiday or vacation, then the computer at Dear Old Mom's is the **local** computer.

Your interpretation of Steps 1-4 is correct.
NOTE: Step2: "So I'd enter this into puTTY, right?", I don't use puTTY, I use a terminal. These are Terminal Commands, so yes, "It seems like your telling the local pc to reboot to the remote" with "ssh -t [email]user@domain.com[/email] reboot" is 100 percent correct.

Forget reboot for now.
It literally will reboot the server, if you have the permission.

"It's just a way of sending your command in" is exactly what this process does.

Step 5+:
ssh -qt [email]user@domain.com[/email] '/path/to/save-all' 
This would be the '/path/to/the/save-all' command that saves whatever save-all saves.

Try this with less invasive or more informative commands like:
ssh -qt [email]user@domain.com[/email] hostname or 
ssh -qt [email]user@domain.com[/email] uptime or
ssh -qt [email]user@domain.com[/email] whoami 

Additionally Step2 will require you enter your password during this process but once it is, you'll never have to again.

re: "Which leaves me rather speechless regarding how you know them off 
hand"... Easy Grasshopper! It gets better but let's get you connected first without your password.

Lemme know.

---

### Post by W@@dy on 2011-01-31
Gah! I forgot to port forward my router so I could connect outside of the internal network.

So where I got confused with the reboot thing,
It could be said like...

ssh -qt [EMAIL="user@domain.com"]user@domain.com[/EMAIL] XXXX

Where XXXX is any old command you want executed, like reboot, or hostname
Yes?

The reason I'm using puTTY is because every other computer I own runs Windows, and one of my classes fiddled around with puTTY, so I went with what I knew best.

Oh! By _"_[EMAIL="user@domain.com"]user@domain.com"[/EMAIL]
You don't mean literally enter that, do you?
It didn't really occur to me before, but it's really just *myusername*@*TheRemotePC'sIPAddress* right?

So this would be sending the command I want to through the designated user's Terminal, just as I want?
So then without that command, it's just like running a program in a different user. Well, not exactly another user,  but on no user. Just in the background sorta.

I like to know what the heck goes on in a PC lol. "It works" is usually never good enough.
Considering it running a Terminal behind the scenes makes sense to me since a Terminal Window doesn't appear on the remote PC. The Terminal is running, but because I didn't tell it to run under "So and So" username, it just runs, hidden from all users.

Hopefully my sister will wake up soon and can open the port for me then I'll repost. I'm subscribed to the thread, but it isn't sending me email notifications as I'd hope. Gotta play with settings some more I suppose.

---

### Post by Habitual on 2011-01-31
> **w@@dy said:**
> gah! I forgot to port forward my router so i could connect outside of the internal network.

So where i got confused with the reboot thing,
it could be said like...

Ssh -qt "user@domain.com" xxxx

where xxxx is any old command you want executed, like reboot, or hostname
yes?

Exactly!

> 
The reason i'm using putty is because every other computer i own runs windows, and one of my classes fiddled around with putty, so i went with what i knew best.
We use what works. It's ok.

> 
Oh! By _"_"user@domain.com"user@domain.com"
you don't mean literally enter that, do you?
It didn't really occur to me before, but it's really just *myusername*@*theremotepc'sipaddress* right?


Not quite.
[email]woody@woodyserver.com[/email] or
[email]woody@ipa.ddr.ess[/email]

> 
so this would be sending the command i want to through the designated user's terminal, just as i want?

That depends on which user's authorized_keys file you copied your id_rsa key into.

> 
So then without that command, it's just like running a program in a different user. Well, not exactly another user,  but on no user. Just in the background sorta.


Sorta. :)

> 
i like to know what the heck goes on in a pc lol. "it works" is usually never good enough.

I knew i liked you!

> 
considering it running a terminal behind the scenes makes sense to me since a terminal window doesn't appear on the remote pc. The terminal is running, but because i didn't tell it to run under "so and so" username, it just runs, hidden from all users.


Hopefully my sister will wake up soon and can open the port for me then i'll repost. I'm subscribed to the thread, but it isn't sending me email notifications as i'd hope. Gotta play with settings some more i suppose.


JJ

Edit: Check your PMs

---

### Post by W@@dy on 2011-01-31
Okay, this is all coming together now.

Final questions,

Will I have to enter in the key each time I use a different local computer to contact the remote pc?
Do I generate a new key each time?
Or do I make the key once, copy and enter it, then never bother with those steps again?

And the "user@domain", I can't imagine this actually creates a domain name for my IP, so using @domain assumes I'm paying for one from GoDaddy or some other company, correct?

My sister is still asleep and sick, so it looks like I won't be able to test this until later

---

### Post by Habitual on 2011-01-31
"Will I have to enter in the key each time I use a different local computer to contact the remote pc?"
and
"Or do I make the key once, copy and enter it, then never bother with those steps again?" 

just take id_rsa with you to use it on another computer.
Make certain to copy it to ~/.ssh (linux) with permissions of 600
```
chmod 600 ~/id_rsa
```
Guard it with your life. 
SSH using the keyfile will NOT work if the permissions on the file are not correct.

"user@domain", I can't imagine this actually creates a domain name for my IP"

If you don't have a domain, then it will have to be IP. (i.e., user@123.456.789.123). It doesn't create any domain for the IP.

Let sleeping sisters lie, I'll be here and so will you. There's time. :)
Take a break, let it settle in. :)

I installed Putty on my linux box here so we can step through it together. The interface is identical on both WinTendo and the Linux platforms, Thank God.

Sis' computer is Windows?

JJ

---

