---
title: "use sed delete everything before the 1st number"
date: 2012-10-11
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-10-11
i need to delete some junk in a line of text there is some kind of special character that does not show up
i need to trim some really strange non-printable character(s) at the front of each line this command generates
```
top -n 1 -u $USER | grep $USER
```this strange character actually uses 3 characters
if i can delete everything before the 1st number i should be good to go

---

### Post by spjackson on 2012-10-11
There's some gubbins at the end of line to remove too.
```

top -n 1 -u $USER | grep $USER | sed 's/^[^0-9]*//' | sed 's/[:cntrl:].*//'

```

---

### Post by pqwoerituytrueiwoq on 2012-10-11
not working :(, BTW you can combine 2 sed commands like this
```
sed 's/^[^0-9]*//;s/[:cntrl:].*//'
```
the pid should be 1st, i think the code to make a line bold is the issue
```
~$ top -n 1 -u $USER | grep $USER | sed 's/^[^0-9]*//' | sed 's/[:cntrl:].*//'
1m 3955 
1834 
1845 
1884 
1887 
1888 
1895 
1897 
1905 
1909 
1911 
1913 


```i am trying to isolate the cpu usage, i did manage to pull it of like this
```
top=`top -n 1 -p "$flash" | grep $USER | head -1 | sed "s/\.//g;s/$USER/\n/" | tail -1 | awk '{print $7}'`
```
i removed the decimals cause bash hates non-hole numbers

---

### Post by drmrgd on 2012-10-11
If you only want to isolate the cpu usage stat, couldn't you just use awk the grab the fields you want?  
```
top -n 1 -u $USER | grep $USER | awk '{ OFS="\t"; print $2,$3,$10 }' -
```

Otherwise, I think it's the color escape characters that you're seeing (maybe a sample of your output would help identify it), and I found this sed command before to help get rid of those characters:

```
top -n 1 -u $USER | grep $USER | sed -r "s/\x1B\[([0-9]{1,2}(;[0-9]{1,2})?)?[m|K]//g"
```

Does that help?

EDIT: Actually might be able to get away with simplifying that a bit:

```
top -n 1 -u $USER | grep $USER | sed -r "s:\x1B\[[0-9;]*[mK]::g"
```

---

### Post by pqwoerituytrueiwoq on 2012-10-11
> **drmrgd said:**
> If you only want to isolate the cpu usage stat, couldn't you just use awk the grab the fields you want? 
cpu keeps changing between 9 and 10 cause of the bold being there sometimes
this is what hte bold keeps doing
```
~$ echo " PID CPU NAME";top -n 1 -u $USER | grep $USER | sed -r "s:\x1B\[[0-9;]*[mK]::g" | awk '{print $2" "$10" "$13}'
 PID CPU NAME
chad 0.0 
1834 0.0 gnome-keyring-d
1845 0.0 sh
1884 0.0 ssh-agent
1887 0.0 dbus-launch
1888 0.0 dbus-daemon
1895 0.0 xfce4-session
1897 0.0 xfconfd
1905 0.0 xfwm4
1909 0.0 xfce4-panel
1911 0.0 Thunar
1913 0.0 xfdesktop
1916 0.0 gvfsd
1920 0.0 gvfsd-fuse
1928 0.0 python
1930 0.0 gmusicbrowser
1932 0.0 pidgin
```

---

### Post by drmrgd on 2012-10-11
I see the problem here.  I'm not sure if this is the expected behavior or not, but I was able to get around this using the '-b' option of top:

```
echo " PID  CPU  NAME"; top -bn 1 -u $USER | grep $USER | awk '{ OFS="\t"; print $1,$2,$9 }' -
```

Does that get you what you're looking for?

---

### Post by pqwoerituytrueiwoq on 2012-10-11
yes, but the column names are wrong
```
echo -e "PID\tCPU\tNAME"; top -bn 1 -u $USER | grep $USER | awk '{ OFS="\t"; print $1,$9,$12 }'
```
bottom line that worked :)

---

### Post by drmrgd on 2012-10-11
> **pqwoerituytrueiwoq said:**
> yes, but the column names are wrong


Whoops!  I was so focused on trying to get rid of those formatting escape characters I forgot to pay attention to the data output!  Glad that worked.

---

### Post by pqwoerituytrueiwoq on 2012-10-11
the content did not matter, just that annoying escaped characters
this is the line i ended up with
```
flash=`top -bn 1 -p "$flash" | grep $USER | head -1 | awk '{print $9*10}'`
```
top on lucid uses a hole number for cpu usage and 12.10 has a decimal, i multiply by 10 to get rid of the decimal to make the number bash friendly
i attached my final script, i made it to stop xscreensaver while flash/parole is running

---

### Post by drmrgd on 2012-10-12
That's pretty cool.  I'm going to try that script out on my home computer.  I think something like that could come in handy!

---

