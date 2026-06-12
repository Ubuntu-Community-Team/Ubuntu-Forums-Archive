---
title: "cvscedega command not found"
date: 2006-03-18
forum: General Help
---

### Post by mitjab on 2006-03-18
0 = Uninstall
   1 = Cleanup
   2 = CVS checkout
   3 = Configure
   4 = Make depend
   5 = Make
   6 = Make install
   7 = Finish up

-------------------------------------------

Installing launcher script ...
    Packing sourcetree...
All done ... CVS installed

   Installed as: cvscedega
   Config path : <homedir>/.cvscedega


then i try
mitjab@ubuntu:~$ cvscedega
bash: cvscedega: command not found


but cvscedega not working?
Why

---

### Post by Lunixfanboy on 2006-03-18
From the look of things, it all went into the .cvscedega subdirectory under your home directory. This subdirectory is not included in the $PATH environment where the command processor looks for files to execute. First thing to try is to change directory into the .cvscedega under your home directory ```
cd /home/yourusername/.cvscedega
``` and then try to execute cvscedega in that directory, telling the command processor to look in that directory for the file to run using ./ like so: ```
./cvscedega
```

---

### Post by mitjab on 2006-03-18
Directory /home/mitjab/.cvscedega does't exist. This is very strange.  I only find .WineCVS directory

---

### Post by Lunixfanboy on 2006-03-18
Did you run the compile script as yourself or as root? If as root, then look in /root for the subdirectory.

---

### Post by mitjab on 2006-03-18
i compile it with mitjab account. I also look in root but no cvscedega directory. what can be wrong?

---

### Post by Ramses de Norre on 2006-03-18
```
sudo updatedb && locate .cvscedega
```

---

### Post by mitjab on 2006-03-18
```

 sudo updatedb && locate .cvscedega
mitjab@ubuntu:~$ cvscedega
bash: cvscedega: command not found
mitjab@ubuntu:~$

```

still the same

---

### Post by Ramses de Norre on 2006-03-18
If locate didn't return any output it means there is no such file in your file system.

---

### Post by mitjab on 2006-03-18
strange, you can se in first post that it was successfuly installed. I choose 0 - cedega_head_userinstall or i must choose 1 - cvscedega_head.

What can i do that cvscedega will work

---

### Post by Ramses de Norre on 2006-03-18
Does locate cedega give any output?

---

### Post by mitjab on 2006-03-18
yes it does

```
mitjab@ubuntu:~$ locate cedega
/home/mitjab/bin/cvscedega
/home/mitjab/.WineCVS/Functions/cedega-config
/home/mitjab/.WineCVS/Profiles/cedega_head_userinstall
/home/mitjab/.WineCVS/sources/cvscedega
/home/mitjab/.WineCVS/sources/cvscedega/.OldState
/home/mitjab/.WineCVS/sources/cvscedega/.TipsScript
/home/mitjab/.WineCVS/installs/cvscedega
/home/mitjab/.WineCVS/installs/cvscedega/bin
/home/mitjab/.WineCVS/installs/cvscedega/bin/wine_relocated
/home/mitjab/.WineCVS/installs/cvscedega/bin/regapi.so
/home/mitjab/.WineCVS/installs/cvscedega/bin/winedefault.reg
/home/mitjab/.WineCVS/installs/cvscedega/bin/config
/home/mitjab/.WineCVS/installs/cvscedega/bin/system.ini
/home/mitjab/.WineCVS/installs/cvscedega/bin/WineCVSFunctions
/home/mitjab/.WineCVS/installs/cvscedega/bin/WineCVSFunctions/Defaults
/home/mitjab/.WineCVS/installs/cvscedega/bin/WineCVSFunctions/cvscedega
/home/mitjab/.WineCVS/installs/cvscedega/lib
/home/mitjab/.WineCVS/installs/cvscedega/man
/home/mitjab/.WineCVS/installs/cvscedega/man/man1
/home/mitjab/.WineCVS/installs/cvscedega/man/man5
/home/mitjab/.WineCVS/installs/cvscedega/include
```

---

### Post by Ramses de Norre on 2006-03-18
```
/home/mitjab/bin/cvscedega
``` Guess that's what you're looking for.

---

### Post by mitjab on 2006-03-18
```

/home/mitjab/bin/cvscedega

```

thx dude. What i mus do that cvscedega will be recognized command. now i must go to bin directory and there run ./cvscedega

What about that some program is not instaled successfuly, how i can remove it with cvscedega?

---

### Post by Ramses de Norre on 2006-03-18
Indeed, you can set it so you can just type 'cvscedega' in terminal. But I have to see my linux to know how to do it and I'm not on it right now.

---

### Post by mitjab on 2006-03-18
np when you will be in it, please look and tell me.
If program is not installed successfuly, then is not instaled or i must remove it?

thx in advanced

---

### Post by Ramses de Norre on 2006-03-18
```
cd /home/mitjab/bin/
./cvscedega
```
Doesn't that work?

---

### Post by mitjab on 2006-03-18
this works yes but just cvscedega not.

---

### Post by FizDev on 2006-03-18
[QUOTE=Ramses de Norre]Indeed, you can set it so you can just type 'cvscedega' in terminal. [/QUOTE]
I believe you just have to copy the cvscedega bin to /usr/bin
Then you should be able to execute it by just typing "cvscedega" in the terminal.

```
sudo cp /home/mitjab/bin/cvscedega /usr/bin
```

---

