---
title: "Custom TTY login name."
date: 2011-09-14
forum: General Help
---

### Post by sptutusukanta on 2011-09-14
At tty login it shows like below:

[B]Ubuntu 11.04 my-pc tty1
my-pc login: _[/B]

I want to change the text "Ubuntu 11.04" & give my own...
How to do that?

Thanks in advance!

---

### Post by haqking on 2011-09-14
> **sptutusukanta said:**
> At tty login it shows like below:

[B]Ubuntu 11.04 my-pc tty1
my-pc login: _[/B]

I want to change the text "Ubuntu 11.04" & give my own...
How to do that?

Thanks in advance!


I am pretty sure it can be done with agetty [http://manpages.ubuntu.com/manpages/hardy/man8/getty.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/getty.8.html)

if you scroll down you can see you can customise a non-standard prompt.

I will leave you to play with that as i dont know exaclty what the commands are to do it right now, i may look back later.

Edit: just found this [http://unix.stackexchange.com/questions/16861/how-to-change-tty-login-prompt](http://unix.stackexchange.com/questions/16861/how-to-change-tty-login-prompt)

not Ubuntu but likely cross distro, as i mentioned above, agetty or in this case possibly mgetty ?

Hope its helpful

peace

---

### Post by sptutusukanta on 2011-09-14
Sorry...

Actually I'm new to Linux. So, it will be helpful it you suggest any tutolials or something like step by step way.

Thank you!!

---

### Post by gmargo on 2011-09-14
That string is generated from the content of the **/etc/issue** file.  
(Except for telnet connections, which uses **/etc/issue.net** instead.)

Here's the default **/etc/issue** for natty:
```

Ubuntu 11.04 \n \l


```You can see the "Ubuntu 11.04" text, which is what you wanted to change.  The backslash sequences are expanded at runtime.  \n is the hostname.  \l is the current tty line.  Other available backslash sequences are documented in the **getty** man page.

So all you need to do is edit **/etc/issue** and modify to your heart's delight.

---

### Post by haqking on 2011-09-14
> **gmargo said:**
> That string is generated from the content of the **/etc/issue** file.  
(Except for telnet connections, which uses **/etc/issue.net** instead.)

Here's the default **/etc/issue** for natty:
```

Ubuntu 11.04 \n \l


```You can see the "Ubuntu 11.04" text, which is what you wanted to change.  The backslash sequences are expanded at runtime.  \n is the hostname.  \l is the current tty line.  Other available backslash sequences are documented in the **getty** man page.

So all you need to do is edit **/etc/issue** and modify to your heart's delight.


ahhh that was easy enough...LOL

well i was kind of along the lines as the etc/issue is mentioned in the link i posted.

cheers though, useful to know.

cheers

---

### Post by sptutusukanta on 2011-09-15
**Thanks all of you!!...**
*Done it finaly!!..*

---

### Post by haqking on 2011-09-15
> **sptutusukanta said:**
> **Thanks all of you!!...**
*Done it finaly!!..*


no worries, thought someone would come in with an easy way ;-)

remember to mark thread as solved using thread tools

cheers

---

