---
title: "scp command question"
date: 2012-07-11
forum: General Help
---

### Post by bol3ez on 2012-07-11
Hello,

I have an ubuntu server that I want to create a script inside, 
so I want to retrieve files from a the remote server (windows), then ...

My problem is how to get this files from the windows server, is scp do the job, if yes tell me how please or if is there another solution ?

thank you.

---

### Post by MG&amp;TL on 2012-07-11
Yes, if there is an ssh server running on the Windows box. Example syntax:

```
scp my-windows-box-ip:/path/to/file /path/to/destination
```

You'll then be asked for a password and then file transfer should commence.

---

### Post by papibe on 2012-07-11
Hi bol3ez. Welcome to the forums!

The easiest way would be to share a directory on the Windows machine, copy the files there, and then in the Ubuntu machine open the Nautilus (file browser) and select 'Go -> Network'.

There you should see the name of the Windows machine, click on it, and gain access to the shared directory.

Hope it helps, and tell us how it goes.
Regards.

---

### Post by bol3ez on 2012-07-11
thank you for response, it seems easy :),

but can you tell me how to know if an ssh box is running in the win machine,
and also how to know the "my-win-box-ip" address ?

---

### Post by MG&amp;TL on 2012-07-11
> **bol3ez said:**
> thank you for response, it seems easy :),

but can you tell me how to know if an ssh box is running in the win machine,
and also how to know the "my-win-box-ip" address ?

Papibe's answer might be easiest for this.

Windows doesn't come with SSH by default, you'll need to install a server program if you want to do this. Which one is up to you.

If you want to find your windows IP address, if you run:

```
ipconfig
```

on the Windows box, the IP should be somewhere in that command.

---

### Post by bol3ez on 2012-07-11
> **papibe said:**
> Hi bol3ez. Welcome to the forums!

The easiest way would be to share a directory on the Windows machine, copy the files there, and then in the Ubuntu machine open the Nautilus (file browser) and select 'Go -> Network'.

There you should see the name of the Windows machine, click on it, and gain access to the shared directory.

Hope it helps, and tell us how it goes.
Regards.

thank you papibe,

in this case I want every time to copy my files in the shared folder, and my needs are to create a script (cron) to do every thing automatically (get files, compile them, send them to a remote server ...), and my problem as I said is to copy this files from the windows machine, that I can complete my job ;)

---

### Post by bol3ez on 2012-07-11
re-hello :)

I tried this : 
```
scp -r user@192.168.1.20://path/to/file ./ 
```

but I get this :  "connect to host 192.168.1.20 port 22: Connection refused" :(

---

### Post by MG&amp;TL on 2012-07-11
> **bol3ez said:**
> re-hello :)

I tried this : 
```
scp -r user@192.168.1.20://path/to/file ./ 
```but I get this :  "connect to host 192.168.1.20 port 22: Connection refused" :(


Hmm. Quick check: do you have an ssh server on that machine?

---

### Post by bol3ez on 2012-07-11
> **MG&TL said:**
> Hmm. Quick check: do you have an ssh server on that machine?

I have installed openssh on windows but the same problem !

maybe I have to activate some things or configure some other ?!

---

### Post by MG&amp;TL on 2012-07-11
> **bol3ez said:**
> I have installed openssh on windows but the same problem !

maybe I have to activate some things or configure some other ?!

Definitely a *server*, right?

You might need to remove some firewall settings. Also, what port is it running on?

---

### Post by bol3ez on 2012-07-11
> **MG&TL said:**
> Definitely a *server*, right?

You might need to remove some firewall settings. Also, what port is it running on?

I didn't understand your question "Definitely a *server*, right?"
I don't know the port that is running for :confused:
but it seems 22 because the error message is "connect to host 192.168.1.20 port 22: Connection refused"

---

### Post by papibe on 2012-07-11
> **bol3ez said:**
> I didn't understand your question "Definitely a *server*, right?"
I believe he wants to make sure you installed the ssh server software, not the more common client.

> **bol3ez said:**
> I don't know the port that is running for :confused:
but it seems 22 because the error message is "connect to host 192.168.1.20 port 22: Connection refused"
The 'client' is attempting to connect using the default port (22). Make sure the server is listening to that port.

Since it's Windows, as MG&TL already stated it, you would need to open your firewall for the ssh server to work. For testing purposes, it would be easy to disable the firewall temporarily.

Regards.

---

