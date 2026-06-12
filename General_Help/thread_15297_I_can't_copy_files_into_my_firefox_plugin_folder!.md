---
title: "I can't copy files into my firefox plugin folder!"
date: 2005-02-13
forum: General Help
---

### Post by pilotcp on 2005-02-13
hello,

one more issue here...i am trying to get the java plugin for firefox, but i am unable to... here is the story.

1.) i downloaded the file
2.) i converted the .bin file to an executable file, and ran it
3.) i read in the instructions that i need to copy two files into the plugin folder, which for me is /usr/lib/mozilla-firefox/plugins. 
4.) i tried to copy the files, but it said i didn't have permission!

now, i've only set up one user on linux, with one name, and one password, and i can't get into this folder!
am i doing something wrong?

Thanks

---

### Post by cblack on 2005-02-13
You don't need to copy them to the firefox plugins dir. Create a symlink.

```

cd /usr/lib/mozilla-firefox/plugins
sudo ln -sf /path/to/javaplugin .

```

---

### Post by evangelion on 2005-02-13
If you're trying to do the copying via command line all you should need to do is put "sudo" before the "cp" command ala
```

sudo cp /path/to/files/ /usr/lib/mozilla-firefox/plugins
then enter *your* password

```
By default everything that isn't in your /home/you folder gets owned by "root" which is the computer admin account, it's there regardless of the account you create and you cannot access its things without the sudo command (this is so you don't accidently delete important things I assume)

If you're more comfortable copying the files with a gui file manager you can do it that way too;  just open up a terminal  and type "sudo nautilus --no-desktop --browser" if you go to "file - new window" you can open up as many root nautilus windows as you need and you'll have root privliages as far as copying.

---

### Post by techn9ne on 2005-02-13
Like osx and other linux systems (except lindows) ubuntu has a root account and disabled login from it. The only way to access it is via sudo or entering your password.

You have a regular user account by default which basically gives you read/write access to your home folder and lets you run programs already installed.

That way logged in as a normal user you can't break the system, install new spyware or viruses.

---

### Post by pilotcp on 2005-02-15
[QUOTE=techn9ne]Like osx and other linux systems (except lindows) ubuntu has a root account and disabled login from it. The only way to access it is via sudo or entering your password.

You have a regular user account by default which basically gives you read/write access to your home folder and lets you run programs already installed.

That way logged in as a normal user you can't break the system, install new spyware or viruses.[/QUOTE]
 so after you put the code in, is there anythin gyou have to do? i made the link, and it appears to have been succesfully created, but firefox still doesn't see it...

---

