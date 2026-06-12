---
title: "Script to zip files from a directory into seperate files"
date: 2011-09-07
forum: General Help
---

### Post by firespydr on 2011-09-07
Hello,

I'm have a directory of mp3 files, which has around 25 files in it. I'm looking to write a script that will zip each mp3 file into its own zip file. I have looked over the zip documentation and man pages and now I'm even more lost. 

The files in question are in the location

/home/chris/Websites/FrankMarzullo/newaudio

The furthest I've gotten is to use the terminal, cd to the directory above, and use the command.

```
$ zip absolsom '/home/chris/Websites/FrankMarzullo/newaudio/absolomspirit.mp3'
```

I can get that to zip up the file, but its creating the directory structure within the zip file. Also I would rather not have to do this a bunch of times since most likely I will be using this script again in the future.

---

### Post by sisco311 on 2011-09-07
```

#!/bin/bash

cd /home/chris/Websites/FrankMarzullo/newaudio || exit 1
shopt -s nullglob

for file in *.mp3
do
    zip "${file%.mp3}" "$file"
done

```

---

### Post by firespydr on 2011-09-07
Thank you, 

Can you explain to me how this works. I can figure most things out in windows, but I'm a linux newb :)

---

### Post by firespydr on 2011-09-07
> **sisco311 said:**
> ```

#!/bin/bash

cd /home/chris/Websites/FrankMarzullo/newaudio || exit 1
shopt -s nullglob

for file in *.mp3
do
    zip "${file%.mp3}" "$file"
done

```

I put this in a file named zip.sh and ran it from the terminal this is what I got back

```
$ sh zip.sh
zip.sh: 4: shopt: not found
  adding: absolomspirit.mp3
```

I cancelled out of that because I wasnt sure what that means, do I need to add something to linux for this to work?

---

### Post by sisco311 on 2011-09-07
Of course. 

the cd command changes the current working directory. 

**command1 || command2** means command2 is executed if and only if command1 returns a non-zero exit status (fails in plain English)

So if the directory doesn't exist the script quits.

*.mp3 expands to the list of .mp3 files: "file1.mp3" "file2.mp3" and so on... 

The for loop runs through the list of words and puts each one in the loop index variable (in our case file), one at a time, and then loops through the body with it.

If there are no .mp3 files in the directory and the nullglob option is not enabled  then *.mp3 is left unchanged the value of the index variable (file) becomes *.mp3, the body of the loop is executed and, of course, zip will probably report a *no such file or directory* error... 

If nullglob is enabled, and there are no .mp3 files in the directory, then the list of files becomes empty and the body of the loop is not executed. **shopt -s nullglob** enables the option.

---

### Post by sisco311 on 2011-09-07
> **firespydr said:**
> I put this in a file named zip.sh and ran it from the terminal this is what I got back

```
$ sh zip.sh
zip.sh: 4: shopt: not found
  adding: absolomspirit.mp3
```

I cancelled out of that because I wasnt sure what that means, do I need to add something to linux for this to work?

sh is not bash. In Ubuntu, sh is a symlink to dash. 

shopt is a bash built-in so you have to run the script in bash:
```
bash ./myscript
```

Or make it executable:
```
chmod +x myscript
```
and run
```
./myscript
```

The first line of the scrip #!/bin/bash, a.k.a shebang, tells to the interpreter, that the script must be executed in bash.  

But if you explicitly, run the script in another shell, like you did( **sh myscript** ), then the shebang is ignored.

---

### Post by firespydr on 2011-09-07
Looks like its working, I had been struggling with this for about 3 hours. Thanks for your help.

---

### Post by sisco311 on 2011-09-07
> **firespydr said:**
> Looks like its working, I had been struggling with this for about 3 hours. Thanks for your help.

You are welcome!

You can improve the script in many ways... For example, it could take the directory name as an argument:
```
#!/bin/bash

if [[ ! -d "$1" ]]
then 
    exit 1
fi

...
```

```
myscript ~/Music
```

If you are looking for a good bash guide, check out the first three links from my signature.

If you have any further questions, please feel free to ask.

---

