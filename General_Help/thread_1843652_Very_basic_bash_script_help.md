---
title: "Very basic bash script help"
date: 2011-09-13
forum: General Help
---

### Post by jwcalifo on 2011-09-13
Hi everyone! I need some help with a very basic bash script.
 
I am creating a script to scan every file on the filesystem for a specific email address which has been used to set up a phishing site on our web server. 
 
I have created an appropriately formatted list, using locate * > files.
 
Now, I need a loop that will read the first line, which is a file path and name, and then cat that file, and then "grep the cat" (lol) to see if there is a match (ie positive output != 0). If there is a match, I want it to echo the LINE (not the grep output but the line itself because it is the filename that I want) to a report file. This is waht I've got so far for this.
 
updatedb
locate * > files
 
for $(cat files | read -r line)
do
if $(cat $line | grep -i [KEYWORD]) != 0
then
echo line >> script_report
fi
done
 
Could someone at least tell me if this is the right way to do this? I consider myself well above novice in Linux, but new to programming. In other words, please TEACH but dont POINT (to FAQs).

---

### Post by sisco311 on 2011-09-13
Not pointing you to FAQ would be hard because the FAQ is in my signature. :)

Check out the BashPitfalls. Every error you made is well documented there. And you made a lot: useless use of cat, no quotes, the for loop is completely wrong... 


I'd try something like this:
```

updatedb
while IFS= read -r -d '' file
do
    read -r line < "$file"
    if [[ "$line" =~ "foo" ]];
    then
        echo "$line" >> script_record
     fi
done < <(locate -0 -q *)

```

If you check out this links you will find out why:
[http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29)
[http://mywiki.wooledge.org/BashFAQ/020](http://mywiki.wooledge.org/BashFAQ/020)
[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)
[http://mywiki.wooledge.org/BashFAQ/031](http://mywiki.wooledge.org/BashFAQ/031)


EDIT: I re-read your post and I'm not sure if I understand correctly what are you trying to do. 

Please explain it in plain English. Thanks!

---

### Post by jwcalifo on 2011-09-13
Thank you. This is a big help. I can look for the specific things in the FAQs that I are new to me, like read, while and if loops.  :)
 
:KS

---

### Post by jwcalifo on 2011-09-13
I just realized you requested more information at the end of your post.  Here goes.
 
I want to scan through every file in the filesystem and look for the word "foo" in every file.  If found, I want it to print out the location and file name that it found "foo".  
 
So it would print out "/home/user/Videos/example.txt".  This would indicate that the word "foo" was found in example.txt in that location.
 
Hope that helps!  Thanks!

---

### Post by sisco311 on 2011-09-14
Oh, I see:
```
while IFS= read -r -d '' file
do
    if grep -i -m1 'foo' "$file"
    then
        printf "%s\n" "$file" >> script_record
    fi
done< <(find / -type f -print0)

```

This will create a list of filenames separated by newlines. But filenames can contain newline characters too, so if you later want to parse the file with a script, then you should separate the filenames with a NUL character:
```
printf '%s\0' "$file" >> script_record
```

Then you can do something like:
```
while IFS= read -r -d '' file
do
    *mycommand* -- "$file"
done< script_record
```

---

### Post by Habitual on 2011-09-15
jwcalifo:

Install rkhunter and scan the system.
```
sudo apt-get install rkhunter
```
After installation, run 
```
sudo /usr/bin/rkhunter --update
```

then check everything with
```
sudo /usr/bin/rkhunter -c
```

After the scan...
```
sudo less /var/log/rkhunter.log
```

Check /var/log/* for evidence of a compromised account (multiple logins for a sole/single user from various IPs).

An uploaded file (notably the Dark Mailer script, usually uploaded as dm.cgi)

Examine output of 
```
last
```

I am subscribed with interest.

Please let us know.

---

