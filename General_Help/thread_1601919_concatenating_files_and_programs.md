---
title: "concatenating files and programs?"
date: 2010-10-20
forum: General Help
---

### Post by nothingless on 2010-10-20
How can I concatenate the standard output of my compiled c program called calc (which takes no arguments) and the contents of files myfile1, myfile2, and myfile3 into one big file? 

I tried:
cat ./calc myfile1 myfile2 myfile3 > bigfile

but that doesn't work...

---

### Post by Barriehie on 2010-10-20
> **nothingless said:**
> How can I concatenate the standard output of my compiled c program called calc (which takes no arguments) and the contents of files myfile1, myfile2, and myfile3 into one big file? 

I tried:
cat ./calc myfile1 myfile2 myfile3 > bigfile

but that doesn't work...

Your question and command look like two diff. things.  Do you want to run the program and have it's stdout concatenated with the other files or do you just want to concatenate the files as you have them listed in your command?


This should run the program and than add the other files.
```

calc > ./somefile && cat ./somefile ./myfile1 ./myfile2 > somebigfile
```

---

