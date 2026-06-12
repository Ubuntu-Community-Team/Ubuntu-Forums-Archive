---
title: "script to find a file or create one &gt;"
date: 2012-04-07
forum: General Help
---

### Post by m_zeid on 2012-04-07
Hello there,

I want to make a script that will ask me for a file name, I enter it, it will search for it.
If it exists it will open the file, if not it will create it for me. or even better it will ask me if i want to create the file or not.


any help is appreciated.

thanks in advance

---

### Post by iponeverything on 2012-04-07
this sounds like homework.

---

### Post by m_zeid on 2012-04-07
> **iponeverything said:**
> this sounds like homework.

kinda 
we had a homework, a different one, and i was chatting with the instructor about the command file and it's various options, and he told me that we can make a bash file for it that find files. and i (fool me) asked what will happen if the file is not found? then he told me to do it, as a challenge!!

i think it's fun to do a research about this, and I'm doing so, but unfortunately a newbie in shell scripts and complex commands and events and such.

---

### Post by iponeverything on 2012-04-07
Here is a hint for you:

stdout
stderr

---

### Post by m_zeid on 2012-04-11
well thanks for your hint, but thats what i did:

```

#!/bin/sh
#!/bin/bash
FILE=unknown

echo "Please enter the file name"
read FILE
if [ -f $FILE ];
then
   echo "File $FILE exists,opening..."
    cat $FILE
else
   echo "File not found, creating a new one..."
    nano $FILE
fi


```

---

### Post by sisco311 on 2012-04-11
I'm glad you figured it out. If you don't mind I have a few suggestions.

By convention, we capitalize environment variables (PAGER, SHELL...) and internal shell variables (RANDOM, BASH_VERSION...). All other variables should contain at least one lowercase letter. Variable names are case-sensitive, so this convention avoids accidentally overwriting environment and internal variables.

Quoting in shell programming is extremely important. You should always use double quotes around shell expansions ( "$file", "$((1+1))" ).

---

