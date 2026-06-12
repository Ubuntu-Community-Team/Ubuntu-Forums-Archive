---
title: "wine problem"
date: 2006-03-18
forum: General Help
---

### Post by mitjab on 2006-03-18
i install wine, then i uninstall it and install it again.

Now when i right click on exe file i can't see install with wine?
how i can now install .exe file?

what can i do?

thx

---

### Post by SoggyCornflake on 2006-03-18
Whenever I run into a problem like that, I open up a terminal window and type the command.  For example wine /home/joe/foo.exe

It probably won't run this way, but you'll be able to see what error messages wine is reporting.  That will tell you what you need to go do.  For example you might be missing a dll file.

---

### Post by mitjab on 2006-03-18
i already try this but not helping me much

```

mitjab@ubuntu:~/PPLIVE,SOPCAST,...$ wine ppstream_1.0.0.151.exe
Warning: could not find DOS drive for current working directory '/home/mitjab/PP LIVE,SOPCAST,...', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\ppstream_1.0.0.151.exe": Module no t found

```

---

### Post by SoggyCornflake on 2006-03-19
> mitjab@ubuntu:~/PPLIVE,SOPCAST,...$ wine ppstream_1.0.0.151.exe
Warning: could not find DOS drive for current working directory '/home/mitjab/PP LIVE,SOPCAST,...', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\ppstream_1.0.0.151.exe":  
What happens if you enter this:  wine .wine/drive_c/windows/notepad.exe

---

