---
title: "Choosing a line from nl command"
date: 2011-08-29
forum: General Help
---

### Post by raith on 2011-08-29
Hi guys

I am trying to write a bash script and am having some trouble. What I want to be able to do is search a directory for a keyword, eg a folder on my desktop and search the keyword readme. I have been able to do and can pipe an ls on a folder to the nl command which lists the numbered files.

What I now want to do is be able to select a number (eg 2) and it will display the ls -l information of the file selected. Does anyone have an idea on what commands to use to do this? I am stuck at how to select a file that has been listed from the nl command.

Thanks for any help!

---

### Post by sisco311 on 2011-08-29
Hi and welcome to the forums!

Please check out the BashGuide, BashFAQ and BashPitfalls at [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)

You could read the files in an array:
```
shopt -s nullglob
cd path/to/dir
arr=(*)

```

Print the content of the array:
```
for ((i=0; i<${#arr[@]}; i++))
do
    printf '%d\t%s\n' $((i+1)) "${arr[i]}"
done

```

then do something like:
```

read -r -p "select file: " nr
ls -al "${arr[nr-1]}"

```

Of course you will have to add some error checks.

---

### Post by raith on 2011-08-30
Thanks! Changing parts around in my script and using the above helped a lot and I have completed what I wanted to make.

---

### Post by sisco311 on 2011-08-30
You're welcome!

---

