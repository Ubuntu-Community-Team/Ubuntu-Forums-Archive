---
title: "Running application as root"
date: 2010-08-28
forum: General Help
---

### Post by computerzworld on 2010-08-28
Hello,
          I am using Ubuntu 8.10 and in my user account which is not root but I am having root credentials. I want to run my openoffice as root user as in my user account openoffice gets crashed as soon as I open it. The same thing is running smoothly when I am logged in as root account. Is it possible to run openoffice as root user without logging out from my user account? Please help me. Thanks in advance.

---

### Post by Dies on 2010-08-28
Running Open Office as root is a pretty silly solution.

Why not post the error you get when you start Open Office as a user?

---

### Post by lisati on 2010-08-28
> **Dies said:**
> Running Open Office as root is a pretty silly solution.

Why not post the error you get when you start Open Office as a user?

Agreed. For everyday tasks, running as root isn't necessary.

---

### Post by WorMzy on 2010-08-28
If you're having issues with open office, try renaming or deleting "~/.config/.openoffice.org" so that you generate a new config.

---

### Post by computerzworld on 2010-08-28
thanks for the reply. Where I will be able to find .config folder?

---

### Post by mendhak on 2010-08-28
Go to Places > Home folder.
Press Ctrl+H  (or View > Show Hidden Files)

You should see .config in there.

---

### Post by computerzworld on 2010-08-28
thanks again.. I have removed .openoffice.org folder from my user. Then it asked me for a fresh configuration. I entered my first name,last name and clicked next , then it gave me error like 

**OpenOffice.org Document Recovery**

Due to an unexpected error, OpenOffice.org crashed. All the files you were working on will now be saved. The next time OpenOffice.org is launched, your files will be recovered automatically.

The following files will be recovered.

---

### Post by WorMzy on 2010-08-28
Strange.

Can you run it from the terminal?:
```
soffice
```

It might give some indication why it's crashing.

---

### Post by computerzworld on 2010-08-28
I got this error when I tried to run OpenOffice using soffice..



terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'

---

### Post by Dies on 2010-08-28
Can you post the output from
```
ls -la ~/.openoffice.org/
```

---

### Post by computerzworld on 2010-08-28
Here is the output of ls -la .openoffice.org


drwxr-xr-x  3 lnx lnx 4096 2010-08-28 14:43 .
drwxr-xr-x 58 lnx lnx 4096 2010-08-28 16:45 ..
drwxr-xr-x  3 lnx lnx 4096 2010-08-28 16:01 3

---

### Post by Dies on 2010-08-28
> **computerzworld said:**
> Here is the output of ls -la .openoffice.org


drwxr-xr-x  3 lnx lnx 4096 2010-08-28 14:43 .
drwxr-xr-x 58 lnx lnx 4096 2010-08-28 16:45 ..
drwxr-xr-x  3 lnx lnx 4096 2010-08-28 16:01 3

That's too bad, I was expecting to see screwed up permissions...

Try moving the folder so that a new one is generated, i.e

```
mv ~/.openoffice.org ~/openoffice.org-possibly_broken
soffice
```

Does it still crash with the same error?

---

### Post by computerzworld on 2010-08-28
I have removed the whole .openoffice.org folder & reconfigured it but the problem remains as it is :(..

---

### Post by Dies on 2010-08-28
> **computerzworld said:**
> I have removed the whole .openoffice.org folder & reconfigured it but the problem remains as it is :(..
Not sure what you mean by "reconfigured" it and IMHO this is still a permissions issue, in any case till you find the right answer I guess it's root for Open Office...
```
gksudo soffice
```

---

### Post by computerzworld on 2010-08-28
I mean I had removed .openoffice.org folder from my user & when I started openoffice again then it asked me for name,email etc. By mistake I called it reconfiguration instead of settings :confused: 

But gksudo soffice is working fine! I think it is opening the application as root. Thanks for that. It had solved my problem for now.

---

### Post by WorMzy on 2010-08-28
I think you're on the right train of thought, Dies. Using "sudo" instead of "gksu" or "gksudo" to launch GUI apps can often cause havoc with permissions and file ownership.

computerzworld, can you run this command in a terminal:
```
ls -Rla ~ > ~/permissions.txt
```

Once it's finished, you'll have a text file in your home directory which has a complete listing of everything in your home folder along with each file's permissions. Open the text file in gedit and do a search (Ctrl+F) for " root " (don't include the quotes, but the spaces are intentional).

You _should_ only get one match, and that's the .. under /home/USERNAME, if you get any others, then those are erroneous and probably what's causing you problems. You'll need to use "sudo chown lnx:lnx /path/to/each/file" to reclaim ownership of each file.

---

