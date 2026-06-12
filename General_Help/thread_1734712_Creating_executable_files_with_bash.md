---
title: "Creating executable files with bash?"
date: 2011-04-20
forum: General Help
---

### Post by javajames97 on 2011-04-20
In windows, you can make a file that runs the contents as if typed out by the user in command prompt by saving the file as either .bat or .cmd . When using BASH in ubuntu, is it possible to save terminal executable files (from a text editor, like GEDIT), What file ending does it take, can i lay it out with just commands? (what is the syntax)

---

### Post by TeoBigusGeekus on 2011-04-20
They are called scripts.
You can put any extension you like (or non at all if you're lazy like me - extensions mean nothing in linux).

A [good startup guide]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") for the command line and script writing.

Something to get you started:

Open a text editor (gedit, geany, nano, vim, emacs, whatever you like). Add these lines in it:
```
#!/bin/bash
echo "Hello world!"
sleep 5
```
Save it as my_first_script on your Desktop.
Make it executable
```
chmod +x ~/Desktop/my_first_script
```
Run it
```
~/Desktop/my_first_script
```

---

### Post by bodhi.zazen on 2011-04-20
If you would like, put your scripts in ~/bin

They will then be added to your path.

/me hates a cluttered desktop =)

---

### Post by Crusty Old Fart on 2011-04-20
> **bodhi.zazen said:**
> If you would like, put your scripts in ~/bin...

Additionally, you might want to consider putting your scripts anywhere you want them, and creating symbolic links (symlinks) to them in ~/bin.

See:
```

man ln

```

---

