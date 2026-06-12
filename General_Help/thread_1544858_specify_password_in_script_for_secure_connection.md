---
title: "specify password in script for secure connection"
date: 2010-08-03
forum: General Help
---

### Post by pmooney78 on 2010-08-03
I'm writing a script that tars, bzips, and encrypts a set of files to my GPG key and then (ideally) uploads the files to a backup directory on my school's web server. I want to run it daily as a cron job. Problem is, the web server only allows connections with scp and sftp. 

Neither program allows specifying a password as a switch. I want to run it as a cron job, so I won't necessarily be present to type the password, and I'd like to just be able to specify the password in the script.

"Ah ha!" you're thinking. "He needs to generate a keypair and set up ssh to not require a password!" And I've found tutorials on the web that show me how to do just that. Problem there is that they all require me to install software and/or access files outside my home directory on the remote machine.

I have zero access to anything other than my own home directory on the remote machine. None. Nada. Zip. I can't install software, access files in /var or /etc, or find out anything about running processes. The local IT priesthood won't give me any information about what's running on the machine or how I can connect to it (and has made a point of telling me that they don't care for Linux users and I should stop asking questions). 

I'd really like to to just be able to specify my password in the script. I understand that scripts are really just text files and that anyone who can get at my desktop computer can read them with a text editor and that this would reveal my password and blah blah blah, but I'm willing to trade that particular risk for the convenience of not having to be awake and monitoring the computer when the cron job is running.

Is there any way to specify the password in the script itself? I'd be happy using either sftp or scp (I've used them both successfully from the terminal to transfer files to this machine). 

I'm still dipping my toes in bash scripting, so detailed instructions would be helpful.

---

### Post by anglican on 2010-08-03
> **pmooney78 said:**
> 
"Ah ha!" you're thinking. "He needs to generate a keypair and set up ssh to not require a password!" And I've found tutorials on the web that show me how to do just that. Problem there is that they all require me to install software and/or access files outside my home directory on the remote machine.


I don't understand your problem here. The server accepts scp/sftp so surely all you need to do is put your key in ~/.ssh/authorized_keys (on the remote machine) which **is** in your home directory (that is ~). Am I missing something?

H

---

### Post by pmooney78 on 2010-08-03
Hey -- you're right! All of the advice I found on the web involved doing some setup on the remote machine, but it turns out that that's all that's necessary. Everything works now, and there's no need to specify the password in the script at all.

Thanks for cutting through the crap for me. :)

---

