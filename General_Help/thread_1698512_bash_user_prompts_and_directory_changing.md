---
title: "bash: user prompts and directory changing"
date: 2011-03-02
forum: General Help
---

### Post by ChimpofDOOM on 2011-03-02
Hey folks

Need your help with a script.. 

Basically I'm trying to create a bash script that'll ask for a folder name and then change into that folder.

```
Not real code but bare with me!

echo "Enter the desired folder and press [ENTER]
read $folder
cd $folder
pwd
/home/<user name>/<whatever the user entered>
```

Is this possible with bash or am I chasing a pipe dream?! 

Thanks in advance!

---

### Post by Mariane on 2011-03-02
I could do this in Perl, giving the user the option to select the directory he/she wants if there are several directories with the same name. Again not code but a hint: 

echo "Enter the desired folder and press [ENTER]
read $folder
find / -name $folder
$path=<the whole string containing the answer>
cd $path

Mariane

---

