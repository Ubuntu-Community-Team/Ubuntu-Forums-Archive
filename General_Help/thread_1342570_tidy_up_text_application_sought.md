---
title: "tidy up text application sought"
date: 2009-11-30
forum: General Help
---

### Post by keevill on 2009-11-30
I'm looking for an application to tidy up text such as removing email indent chevrons and blank lines etc.
Any ideas - tried Googling but so far nothing comes up.

---

### Post by kaibob on 2009-12-01
> **keevill said:**
> I'm looking for an application to tidy up text such as removing email indent chevrons and blank lines etc.
Any ideas - tried Googling but so far nothing comes up.
I understand that you are looking for a dedicated application that will do what you want. I recall many such applications from my Windows days but don't remember any for linux. Perhaps, with this bump, another forum member will be able to suggest one.

If an application is not available, you may want to consider a small shell script. For example, the following command removes all > characters and blank lines, and squeezes consecutive spaces. After making whatever additions you like, you could make this into a Nautilus script, which would allow you to clean up a file with just a right- and then left-click in Nautilus. 

```
sed -i 's/[<>]/ /g ; s/ * / /g ; s/^ // ; /^$/d' file
```

Just to get an idea of how this would work, create a file with one of your emails. Give it the name file. Then open a window, change to the directory that contains the file, and enter the above command. The -i option directs sed to overwrite the existing file.

EDIT:
I modified my original command line for my own use. It now deletes the characters < and >; squeezes two or more spaces into one; removes spaces from the front of all lines; and removes blank lines. You can remove other characters by adding them to [<>]. For example, to remove < and > and ~ and `, you would use [<>~`]. To make this into a nautilus script, change file to "$1".

---

### Post by keevill on 2009-12-01
> **kaibob said:**
> I understand that you are looking for a dedicated application that will do what you want. I recall many such applications from my Windows days but don't remember any for linux. Perhaps, with this bump, another forum member will be able to suggest one.

If an application is not available, you may want to consider a small shell script. For example, the following command removes all > characters and blank lines, and squeezes consecutive spaces. After making whatever additions you like, you could make this into a Nautilus script, which would allow you to clean up a file with just a right- and then left-click in Nautilus. 

```
sed 's/>//g ; /^$/d' file | tr -s ' ' > newfile
```

Just to get an idea of how this would work, create a file with one of your emails. Give it the name file. Then open a window, change to the directory that contains the file, and enter the above command. Then look at newfile to see how it looks.

well thx for the reply but that's a bit long-winded for my needs.
I really want something with a nice old fashioned GUI.

---

### Post by keevill on 2009-12-02
Solved.
I installed clippy.exe using Wine and it works fine.
-keevill-

---

