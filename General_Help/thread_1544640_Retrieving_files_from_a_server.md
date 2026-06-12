---
title: "Retrieving files from a server"
date: 2010-08-02
forum: General Help
---

### Post by themusicalduck on 2010-08-02
I'm trying to copy some files from a server at my University onto my PC. They gave me a script that is supposed to allow me to copy the files, but it won't work. It won't accept my password for some reason and allow me access.. :/ The university support don't seem to know why it won't work.

What I can do is ssh into the server without the script and navigate my files with the command line. The thing is, I need to first ssh into a 'remote access server' and then from that, ssh again into the server which has my files on. I can also move and copy the files around my homespace on the server once I'm logged in.

I've tried using scp to copy files from the one server to my PC. Using ```
scp -r username@server:/path/to/folder theo@mydydns:/home/theo/Desktop
``` and I've tried just ```
scp -r /path/to/folder theo@mydydns:/home/theo/Desktop
``` both while logged into the server with my files on through the remote access one, but on the first command I get a permission denied error and trying the second command, I get no output or error, but nothing transfers anyway.

I know my PC is accepting ssh requests as I can ssh in with putty off my phone.

I'd really like to persuade this to work, because the only other way to get hold of the files is by driving 70 miles and copying them over onto a pendrive :P

---

### Post by AlphaLexman on 2010-08-02
'scp' is a tool that uses 'ssh'...
i.e. you don't have to 'ssh' into the server first, just run the 'scp' command from a local terminal.

---

### Post by themusicalduck on 2010-08-02
> **AlphaLexman said:**
> 'scp' is a tool that uses 'ssh'...
i.e. you don't have to 'ssh' into the server first, just run the 'scp' command from a local terminal.

Problem is that I don't have an address to directly connect with the server with my files on. I have to ssh into another server first, and then ssh into the right server from there using just the name of the server.

I don't think you can ssh directly into it from a local terminal. I assume it's a security thing they have set up. If I try the command while logged into the remote access server, then it doesn't recognise the command.

---

### Post by Smart Viking on 2010-08-02
And you could maybe give us the script, to look for errors. :) (and to please my curiosity :P)

---

### Post by themusicalduck on 2010-08-02
> **Smart Viking said:**
> And you could maybe give us the script, to look for errors. :) (and to please my curiosity :P)

I'd like to :P but I don't think they'd like me to share it seeing as it grants external access (only with the right password mind) to their servers. You can only download it from the uni intranet so I don't think they'd want me to post it online.

A bit annoying, because I do want to know why it won't work :)

---

### Post by AlphaLexman on 2010-08-02
You don't happen to be attending a university in Redmond, Washington? :D

---

### Post by themusicalduck on 2010-08-02
Err, not quite :) I'm at UWE in Bristol, England.

---

