---
title: "ssh - sharing private key with host"
date: 2011-05-31
forum: General Help
---

### Post by bionicdude on 2011-05-31
Hey,

I've recently entered the world of android.
I use ConnectBot to ssh into my main server and run a command.
The command is an alias as per below:
alias motionoff='pkill motion;ssh -t -p 24 192.168.15.7 '\''pkill motion'\'''

as you can see, it kills the motion process locally and then kills the one running upstairs.

When i used to connect in and run this, it would kill the local process and then ask me for the passphrase to unlock my private key so that it could connect upstairs via ssh.

Now when i use connectbot the following happens:
issue ssh connect command
connectbot asks for passphrase to unlock private key
I input private key
I run the motionoff alias on my server
connectbot asks if it's ok to allow the remote host to use my private key
I say yes and I don't have to input my passphrase again.

I really like this and I've been desperately trying to search for how to do this from other linux boxes.

Both my machines run ubuntu (10.10 and 11.04)

So in summary:
How can I allow a remote ssh host to use my local private key when "piggybacking" onto another system?

Thanks in advance for any pointers you can offer

---

### Post by bionicdude on 2011-06-27
well I feel somewhat silly..

Having read the man for ssh, I spotted the -A switch.
i must have tried dozens of google searches with all kinds of keywords too...

There are some security risks/issues, but for what i need - this is exactly the job.

---

