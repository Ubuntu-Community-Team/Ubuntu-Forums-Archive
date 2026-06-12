---
title: "Help with Terminal command to locate accurate DMI Table."
date: 2012-09-24
forum: General Help
---

### Post by patriot56 on 2012-09-24
Hello forum.
I am trying to access the DMI Table for my computer using a Terminal command and I would like to pipe (|) it to, say, a .txt file?
So far, I have used the following command: (*I realize that ("| less") only makes the output easier to read through*).
```
dmidecode -q | less
```but I don't know how to get the output to the .txt file destination.  I am still learning the Terminal so any help you can offer is appreciated.
According to the **man** page for "dmidecode" the output is most often just plain incorrect.

Is there a better, command that I should be using to obtain an accurate DMI Table, and how do I send the output to a file?

As always, thanks for the help in advance. :)

---

### Post by Vaphell on 2012-09-24
to redirect output to file simply end your command with **> file.txt**

---

### Post by patriot56 on 2012-09-24
> **Vaphell said:**
> to redirect output to file simply end your command with **> file.txt**
Thanks Vaphell, I'll give that a go.

---

### Post by patriot56 on 2012-09-25
Just to update my previous post.
When I enter the following code: ```
sudo dmidecode -q | > /home/*myname*/Desktop/SystemInfo/IBM_Computer.txt

```and browse to the location of the text file, I see that the file "IBM_Computer.txt" has been created in the correct directory however, it is empty. 
None of the data that dmidecode should have fetched, was written to the file?? :(
Anyone have any suggestions?  I am sure that it is because I am missing an important element in the code but I don't know what it is.

Normally I wouldn't even bring this problem to the Forum for help but I have searched around the Internet and am unable to locate an answer to this problem; not one that works anyhow.  *That problem being, a way to get accurate DMI Table data into a .txt file.*

Thanks again, any help is greatly appreciated.

---

### Post by patriot56 on 2012-09-25
**[SIZE=3]I was able to figure it out![/SIZE]**
After complete frustration trying to get the output of the *dmidecode*  to copy to the .*txt* file that I created, I simply "copied & pasted" the output from the Terminal to the file.
:confused: -- I don't know why I didn't think of doing that sooner.  I guess I like doing things that hard way. ](*,)
Plus, I am still learning my way around the Terminal. 
In-spite of it all...I do prefer CLI over GUI.

---

### Post by Vaphell on 2012-09-25
| is only required when you pass stdout to stdin of another command
redirection to file is simply > file, with no |

---

### Post by HiImTye on 2012-09-25
your issue was that you were trying to pipe the output, with no pipe destination. if you did this instead:
```
sudo dmidecode -q > /home/myname/Desktop/SystemInfo/IBM_Computer.txt
```then it would have functioned the way that you wanted it :)
just for reference, you *pipe* (|) the output to a program and *redirect* (>) the output to a file. you can also *append* (>>) the output to an existing file, without deleting the original file contents :)

---

