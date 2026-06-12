---
title: "freenet and frost????"
date: 2010-08-07
forum: General Help
---

### Post by choochoousmc on 2010-08-07
friend suggested I D/L freenet so I did.
It has it's possibilites of being useful. But is very slow and clunky and difficult to navigate.
But I see from wikipedia companion software   FROST makes searches and uploads and downloads easier.
So I D/Led that.
I created a separate directory for it  /home/downloads/frost
I opened the zip file and extracted to that location.

But I don't see an actual "install" file.
Double clicking the *.sh  files opens a text file but does not run.
A read me file says to go to terminal and type in "chmod +x *.sh"

This will "activate"  *.sh to "run" like an executable.
I did that no changes.
It also says to CD to the Frost directory
I keep getting directory / location does not exist.

So could someone please tell me what to do to install and run the program?
The commands I may need to type in the terminal?

Thanks

---

### Post by choochoousmc on 2010-08-07
my terminal says this

choochoo@choochoo-acer:~$ cd /choochoo/downloads/frost
bash: cd: /choochoo/downloads/frost: No such file or directory
choochoo@choochoo-acer:~$ 
choochoo@choochoo-acer:~$ cd /choochoo/downloads
bash: cd: /choochoo/downloads: No such file or directory
choochoo@choochoo-acer:~$ 

but yet if I click "places"   home folder it opens a browser window.
My home folder is choochoo
and I have a icon view in right pane. downloads  is a folder there
in it is frost

so why does terminal keep saying doesn't exist?

---

### Post by alecz20 on 2010-08-30
Your home folder is actually in 

```

/home/choochoo

```

Maybe try this:

```

cd ~/downloads/frost

```

~ means your home directory

---

