---
title: "Restore the sudoers, &quot;sudo chmod 777 -R /.*&quot; fatal command"
date: 2011-10-02
forum: General Help
---

### Post by oscarblo on 2011-10-02
Hi!

I know, I'm crazy, I wrote the command

[FONT="Courier New"]sudo chmod 777 -R /.*[/FONT]

in my ubuntu server, its a fatal command :cry:

Now my [FONT="Courier New"]etc/sudoers [/FONT]file and [FONT="Courier New"]etc/sudoers.d[/FONT] folder are blocking any operation on my server, even I'm not able to connect by FTP or SSH to the server. I was able to change the permissions of the[FONT="Courier New"] sudoers[/FONT] to the[FONT="Courier New"] 0440[/FONT] but even now it is still not fixed. Now Im not able to logging remotely to the server, but Im going to have access to the physic machine next days, but any way I don't know what to try..
I will be really thankful if someone can help me, or give some ideas what to do, otherwise I will have to format, and even Im not able to copy the files to backup the information needed :(

best regards!
Oscar

---

### Post by matt_symes on 2011-10-02
Hi

Personally, i would backup from a LiveCD and reinstall as it's a potential security risk on a server.

Anyway for ssh...

```
matthew@matthew-laptop:~/.ssh$ ls -l
total 12
-rw-------. 1 matthew matthew 1675 2011-04-19 16:54 id_rsa
-rw-r--r--. 1 matthew matthew  404 2011-04-19 16:54 id_rsa.pub
-rw-r--r--. 1 matthew matthew 3306 2011-09-28 11:52 known_hosts
matthew@matthew-laptop:~/.ssh$ 
```

Kind regards

---

### Post by oscarblo on 2011-10-02
Thanks Matthew,

It's good hear that from live CD I can have the chance to backup my data :)

I didnt get the ssh sugestion,
In my local machine I only can find the ```
/home/oscar/.ssh/known_hosts
``` file, the others are missing. Its supost to do something to this file, like drop the generated keys??

Really, I have a very important missing time factor, and right now this is a server just for develop and show the product, and the security is not yet "important" in this stage, if there is another fast way to go, in this stage will be better.

Thanks,

Best regards.

---

