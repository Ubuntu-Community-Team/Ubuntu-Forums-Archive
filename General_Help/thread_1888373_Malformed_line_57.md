---
title: "Malformed line 57"
date: 2011-11-29
forum: General Help
---

### Post by langner on 2011-11-29
Hi All,

While I was trying to fix another error with the key signatures. I believe I deleted one that I shouldn't of. 

Now I get this error and the update manager doesn't open any more. Screen shot included. The error message below is from the terminal window.  

[I]E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.[/I]

HELP! I DON'T KNOW WHAT TO DO?

Thanks for you help in advance.

Matthew

---

### Post by mcduck on 2011-11-29
You could start by opening the file the error message tells you (/etc/apt/sources.list), and looking at the line 57... ;)

If you can't spot the problem, then post that line (or the whole file) here.

---

### Post by langner on 2011-11-29
Hi, 

Thanks for getting back to me.

Here is the line, I think but please check.

*deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric*

I have uploaded a copy of the file in a txt format. I think that I can copy and paste the code back if needed.

Thanks

Matthew

---

### Post by langner on 2011-11-29
Ok, I said I could copy the changes back into the file above, but it is read only and I don't know how to get round it. 

I'm so noob at this :-(

---

### Post by mcduck on 2011-11-29
It's not read-only, you just haven't opened it with suitable permissions to overwrite the file... ;)

Pop open a terminal and run "gksudo gedit /etc/apt/sources.list" to open the file for editing with admin permissions. Then add a "#" (witout the quotes) to the beginning of lines 57 and 58. Then save the file, and run "sudo apt-get update". That should fix the problm, but if you get any errors, please post them here.


...and to help with the permissions thng in the future, you might want to read this document about how adminstartion tasks and admin permissions are handled in Ubuntu: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by ajgreeny on 2011-11-29
The line ```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric
```should have something else at the end, which you must have removed when you were doing whatever you did.  If you can remember what you changed, you can edit the file again back to what it was with command ```
gksu gedit /etc/apt/sources.list
``` but I think line 58 may be similarly incorrect.

If you can not sort this easily this way you can get a complete new sources.list file by going to [Sources List Generator]("http://repogen.simplylinux.ch/")  and ticking in the boxes as you want, then replacing your current file with the newly generated one.

Just rename the old one in case you need to restore it.

---

### Post by matt_symes on 2011-11-29
Hi

The line is malformed because it does not know which repository you want to use (main, universe, multiverse or restricted).

It should look some thing like

```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric **main**
```

where main is the repository.

If you fancy learning the terminal

This will display lines 57 and 58 from the file.

```
sed -n '57,58p' /etc/apt/sources.list
```

If you are happy they are incorrect then

```
sudo sed -i '57,58d' /etc/apt/sources.list
```

This will delete both the lines after you have entered your password.

Kind regards

---

### Post by langner on 2011-11-29
Thanks all, 

I'll have to do all that you have mentioned when I get back home tonight. I'll post my results either tonight or tomorrow. 

Thanks again

---

### Post by langner on 2011-11-30
I just want to say, THANKS ALL FOR YOUR HELP.

I used the sources list generator as suggested by ajgreeny and it all work well now. I did comment out line 57 and 58 first and that did sort the problem, (that I made some how), but I was left with my original problem. This been that the signature key didn't work. 

By following the instruction from the link below, adding a new list and keys, there are no more errors.

Time now for :popcorn:  

> **ajgreeny said:**
> 

If you can not sort this easily this way you can get a complete new sources.list file by going to [Sources List Generator]("http://repogen.simplylinux.ch/")  and ticking in the boxes as you want, then replacing your current file with the newly generated one.

Please give your self a pat on the back for a job well done. :)

---

