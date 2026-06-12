---
title: "Question about tar"
date: 2012-06-20
forum: General Help
---

### Post by xuyuangogogo on 2012-06-20
Hi, guys!

I am a rookie in Ubuntu. I tried to understand the following code but apparently I can do nothing about it. I've checked the manual but still I cannot understand it.

Could you please explain what does the code mean?

system("tar cvzf ".$path."tmp/`date +%Y%j%k%M%s`.tar " .$path."*.*");

Thanks you very much!

---

### Post by hunter.allen on 2012-06-21
system("tar cvzf ".$path."tmp/`date +%Y%j%k%M%s`.tar " .$path."*.*");

Firstly, I have no idea what language you are using here. 

Let's dissect the command. 

tar cvzf ~ "tar -cvzf" which compresses it's argument into a file. 

$path ~ $PATH which is the PATH variable for your install (in ~/.bashrc)

I need some more information to help you... In what context do you use this code?

---

### Post by Lars Noodén on 2012-06-21
The system() function is from some programming or scripting language.  

The whole thing seems to make a tar archive with the date in the file name. You can get the breakdown of the date format by looking up the manual page for [date](http://manpages.ubuntu.com/manpages/precise/en/man1/date.1.html).   The contents of the archive will be copied from whatever is in $path.

---

### Post by rukiaEnix on 2012-06-21
It's PHP.

As I see it compresses your $PATH and saves it at tmp  using the format of the date.

---

