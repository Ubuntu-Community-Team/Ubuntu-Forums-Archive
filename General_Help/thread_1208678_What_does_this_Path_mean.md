---
title: "What does this Path mean?"
date: 2009-07-09
forum: General Help
---

### Post by antdgar on 2009-07-09
I'm following a user guide about how to configure the IRC client IRSSI.

It says place a text file here: [I]
~/.irssi/config[/I]

where is that? I don't understand what the curly line means. I searched for '.irssi. but it could not find the folder...Does anyone how I can get to that .irssi folder?

PROBLEM SOLVED. THE FOLDER WAS HIDDEN XD

---

### Post by Soul-Sing on 2009-07-09
homemap: ctrl+h ===> voila

---

### Post by slugmax on 2009-07-09
The '~' is called a tilde, and it just means 'home directory'. So if your user's home directory was '/home/antdgar', you would edit the file '/home/antdgar/.irssi/config'. The shell knows what the tilde means, so you can do something like (substitute 'emacs' with your favorite text editor, like vim, nano, or gedit)

```

cd ~/.irssi
emacs config

```

or directly:

```

emacs ~/.irssi/config

```

If the '.irssi' directory is not there, you need to create it:

```

mkdir ~/.irssi

```

---

### Post by issih on 2009-07-09
Ok..in case thats not quite enough info.

First of all, the symbol "~" dynamically maps onto the current user's home diectory, so if you are logged in as user "bob", then:
```
~/movies
```
and:
```
/home/bob/movies
```
are equivalent paths.

Now secondly, linux by default hides any files or directories that start with a period character "." This is true in the terminal with ls (use the -a flag to see the hidden files) or in the nautilus file browser (hit ctrl-h to see them).

So in conclusion that path is to a file called config in the hidden folder .irssi which resides in your own home folder.

Hope that helps

---

### Post by Wim Sturkenboom on 2009-07-09
**~** indicates your homedirectory. Directories starting with a dot are hidden. You need the -a option for the ls command (or configure the file browser (e.g. nautilus) to show hidden files) if you want to see it.

---

### Post by Dragonbite on 2009-07-09
~ means the same things as /home/yourusername

So it goes to /home/tim for Tim and /home/sally for Sally but the script/program only has to use the tilda (~) and let the system figure out which folder that is in.

---

