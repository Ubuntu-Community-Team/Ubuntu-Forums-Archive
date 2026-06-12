---
title: "Convert Bash Into Executable File."
date: 2010-01-19
forum: General Help
---

### Post by Chamillionaire2 on 2010-01-19
What's Up?

OK, SO I'm not talking about changing the file permissions, The only thing I could find on google was this [http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1263931666197+28353475&threadId=1192978](http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1263931666197+28353475&threadId=1192978)

Basically can you convert your bash script into a executable file, One that you can't open in text editor?

Thanks Bye.

---

### Post by Cabs21 on 2010-01-19
```
chmod +x Path/to/file/you/want to/make/executable.file
```

that will tell ubuntu to ask if you want to run, open and run in terminal, open and edit via text editing, or cancel, every time you execute the file from nautilus.

---

### Post by capscrew on 2010-01-19
> **Chamillionaire2 said:**
> What's Up?

OK, SO I'm not talking about changing the file permissions, The only thing I could find on google was this [http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1263931666197+28353475&threadId=1192978](http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1263931666197+28353475&threadId=1192978)

Basically can you convert your bash script into a executable file, One that you can't open in text editor?

Thanks Bye.

@Cabs21 has described how to make a text file script executable.  But this will not help you with your second request (i.e  "One that you can't open in text editor")  That type of file would be a binary file and that would have to be compiled.

Text fie scripts are parsed by the bash shell or an interpreter such as PERL or Python. Binary files do not need an interpreter (e.g. any C or C++ binary file).

In other words the fact that it is "executable" is not the whole story.  BTW there are other non executable binary files (e.g. .jpg or .osd)

---

