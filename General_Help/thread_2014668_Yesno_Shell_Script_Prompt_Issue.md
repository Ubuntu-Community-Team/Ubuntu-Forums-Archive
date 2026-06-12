---
title: "Yes/no Shell Script Prompt Issue"
date: 2012-07-02
forum: General Help
---

### Post by rhss6-2011 on 2012-07-02
I'm trying to create a **yes/no prompt** within a shell script that I'm making for someone else and it's starting to get irritating right now... I've been up and down the forums, checked my 833 page PDF book on Bash/Shell scripting for reference and I can not get this to work at all...
Every time I build a **script with various aspects** to it I test it out piece by piece. I usually use Zenity for prompts and other scripts, but this is for someone who doesn't have it installed on their system. So far **everything works until the yes/no prompt** here.

Here's the ***NOT WORKING*** test prompt:

```
#!/bin/bash
read -p "Yes or no? If you don't know please type 'no': " prompt
if [ $prompt == [Yy][Ee][Ss] ] ; then
    #Execute desired command if user agrees.
    printf "Thank you, please wait one moment \n"
    sleep 2
    #Execute functions
    function1
    sleep 2
    function2
    sleep2
    printf "Everything worked just fine without any errors, have a nice day!"
else
    #Exit if user decided against the action
    printf "Thank you for your time, have a nice day \n"
fi
```***My terminal output*** is

```
test.sh: 3: [: yes: unexpected operator
No worked just fine
```The crazy thing is, I** tested the function** which **works**, I **tested** it **using** my zenity prompt, but as soon as I use my **prompt** **above**, it **stops working**! 
Can anyone offer me some  help or suggestions?

---

### Post by rai4shu2 on 2012-07-02
Why not just check for "y" or "n"? Then it's a simple case of:

```
if "$prompt" = "y"; then
```

---

### Post by steeldriver on 2012-07-02
I think you might need to use the double bracket [[ ... ]] syntax (aka extended test) to get the regex test to work

```
if [[ $prompt == [Yy][Ee][Ss] ]] ; then

```

---

### Post by rhss6-2011 on 2012-07-02
Thanks Steel diver but that** didn't work either**
I tried that before, and just now but:

```

Yes or no? If you don't know please type 'no': **yes**
**test.sh: 3: test.sh: [[: not found**
Thank you for your time, have a nice day
```@rai4shu2

I want to make sure that anyone who types "yes" with caps or no, or whatever that it will work...

---

### Post by steeldriver on 2012-07-02
well it works for me... I copied your exact script and modified it (no spaces between the [[ btw i.e. '[[' and ']]' are **keywords** not literal brackets) 

```

#!/bin/bash

read -p "Yes or no? If you don't know please type 'no': " prompt
if [[ $prompt == [Yy][Ee][Ss] ]] ; then
    #Execute desired command if user agrees.
    printf "Thank you, please wait one moment \n"
    sleep 2
    #Execute functions
    function1
    sleep 2
    function2
    sleep2
    printf "Everything worked just fine without any errors, have a nice day!"
else
    #Exit if user decided against the action
    printf "Thank you for your time, have a nice day \n"
fi

```

---

### Post by sisco311 on 2012-07-02
[[ is a bashism. It doesn't work in dash (sh is a symlink to dash in Ubuntu). ;)

I'd use a case statement
```
read -r ans
case $ans in
    [yY]|[yY][eE][sS])
        do something
        ;;
    [nN]|[nN][oO])
        do something else
        ;;
    *)
        whatever
        ;;
esac

```

---

### Post by rhss6-2011 on 2012-07-02
I don't get it...** I copied EXACTLY what you have**, then:

```
usr@usr:path/to/script$ **sh test.sh**
Yes or no? If you don't know please type 'no': **yes**
[B]test.sh: 4: test.sh: [[: not found
Thank you for your time, have a nice day [/B]
usr@usr:path/to/script$ 
```

---

### Post by sisco311 on 2012-07-02
sh is NOT bash.

---

### Post by rhss6-2011 on 2012-07-02
Oh wow... I typed "bash test.sh" and it worked... Why does it do that if both commands run it!?!?

---

