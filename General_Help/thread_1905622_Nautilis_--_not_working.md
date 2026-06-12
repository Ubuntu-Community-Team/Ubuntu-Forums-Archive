---
title: "Nautilis -- not working"
date: 2012-01-07
forum: General Help
---

### Post by mk5500 on 2012-01-07
How can I delete a couple of files in my root  in etc/init.d ?

I tried Nautilis (sp?) and it prompted for my password and I still get permission denied.

I tried terminal, going to the init.d folder and using rm and still no go.

If I can't get this solved I'll have to reinstall because I have a program autostarting that I now want to get rid of.

THANKS.   Does using Lubuntu have something to do with it?

I'm a Linux novice -- so please make this easy if you can.

---

### Post by deonis on 2012-01-07
use mc (sudo apt-get install mc). Of course you will need to run mc with  sudo in terminal. You can do the same thing with Nautilus. But if you want to remove one file in any root folder you just type the following in terminal: sudo rm /path/to/file

---

### Post by mk5500 on 2012-01-07
"you just type the following in terminal: sudo rm /path/to/file"

that worked fine.

you know what? I think I left out "sudo"

-- Mr Embarrassed

what is sudo short for anyway? something that dates back to early days of Unix no doubt?
EVERY command must start with it?

I noticed I can access mplayer by just typing mplayer -- so applications don't need it?

---

### Post by pretty_whistle on 2012-01-07
> **mk5500 said:**
> "you just type the following in terminal: sudo rm /path/to/file"

that worked fine.

you know what? I think I left out "sudo"

-- Mr Embarrassed

what is sudo short for anyway? something that dates back to early days of Unix no doubt?
EVERY command must start with it?

I noticed I can access mplayer by just typing mplayer -- so applications don't need it?
Every command must start with it?  No.

---

### Post by pretty_whistle on 2012-01-07
> **mk5500 said:**
> "you just type the following in terminal: sudo rm /path/to/file"

that worked fine.

you know what? I think I left out "sudo"

-- Mr Embarrassed

what is sudo short for anyway? something that dates back to early days of Unix no doubt?
EVERY command must start with it?

I noticed I can access mplayer by just typing mplayer -- so applications don't need it?
Applications only need sudo first if you're needing to run the application as root.

---

