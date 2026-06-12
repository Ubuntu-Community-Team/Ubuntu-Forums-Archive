---
title: "Driven Nuts!"
date: 2011-02-10
forum: General Help
---

### Post by rlb.contact on 2011-02-10
I cannot figure out, for the life of me how to restrict certain programs to certain users. I have a admin account, with various accounts for family and friends. I want to simply keep some programs (such as multiple browsers) from appearing and being available in simple accounts. I want others to have more freedom minus the admin abilities. And finally I want to prevent co-mingling of data between the copies of each version of a user's program.

For example, I have both chrome and firefox on a laptop. I do not want the headache of undoing damage that people have made with chrome or answering their questions. How do I strike both the menu item and and actual program from their access/programs available. I also don't want them to look backwards and wreak havoc on other's email (it's happanened.)

It must be simple, I can not find the info on the boards so it has to be something dealth with years ago.

Please help.
Lee

---

### Post by mister_p_1998 on 2011-02-10
Im only guessing, but do you have to create a group and add users to it? that sort of thing?

Steve

---

### Post by amsterdamharu on 2011-02-10
> How do I strike both the menu item and and actual program from their access/programs available.

I guess log in as the user and remove it, create groups for programs, add users to those groups and then give that group execute permission on the program.

> I also don't want them to look backwards and wreak havoc on other's email (it's happanened.)

That does sound rich, if a user logs in preferences of the program including browser history are saved in the users home folder. Remove other users from accessing these folders (even read permission) and it should be fine. But antecedently going into another users email just because you use the same browser sounds ridiculous.

---

### Post by 3Miro on 2011-02-10
Check umask, so that people cannot look into each other's files. Check information on groups/user/other and how to use those to restrict users from running programs and such.

---

### Post by CrusaderAD on 2011-02-10
lockdown editor has some cool features. It's in the Ubuntu Software Center.

---

### Post by rlb.contact on 2011-02-13
>  That does sound rich, if a user logs in preferences of the program including browser history are saved in the users home folder. Remove other users from accessing these folders (even read permission) and it should be fine. But antecedently going into another users email just because you use the same browser sounds ridiculous.

Indeed, it was on another OS. They were password issues. I am learning more about the admin side of Ubuntu for fun. 

>  That does sound rich...

Thanks for the insults. It's always good to make fun of learners.

---

### Post by ankspo71 on 2011-02-13
> **rlb.contact said:**
> I cannot figure out, for the life of me how to restrict certain programs to certain users.

these links might help:
[http://askubuntu.com/questions/8149/how-can-i-restrict-program-access-to-other-users](http://askubuntu.com/questions/8149/how-can-i-restrict-program-access-to-other-users)
[http://www.webupd8.org/2009/07/restrict-lock-your-ubuntu-desktop-with.html](http://www.webupd8.org/2009/07/restrict-lock-your-ubuntu-desktop-with.html)
[http://blog.bodhizazen.net/linux/how-to-restrict-access-with-rbash/](http://blog.bodhizazen.net/linux/how-to-restrict-access-with-rbash/)

---

### Post by amsterdamharu on 2011-02-13
> Thanks for the insults. It's always good to make fun of learners.

Sorry, wasn't meant that way. I mean that it sounds unlikely that that would happen on Ubuntu for the reason already given.

I wasn't out to insult you but might have expressed it differently like "are you sure that's what happened on an Ubuntu install?"

Wasn't aware you are a new user and some people might come across something that is unlikely to happen/didn't interpret it correctly. Hence the expression it sounds rich. I am not native English but thought it means something like that's unlikely.

---

### Post by HermanAB on 2011-02-13
Howdy,

That is what sudo does.  It provides fine grained control over who can run which programs.  Read the /etc/sudoers file, it is quite self explanatory, since there are many examples inside it.

---

### Post by grahammechanical on 2011-02-13
Hi rib.contact

I assumed from reading your first post that you were talking about people using the same computer. On Ubuntu every user has their own Home folder where their emails are stored. I assume that Ubuntu would only allow access to these user home folders to the administrator. But in one of your other posts you mention someone gaining access from another OS. Is that on another computer? Is this an issue of network access?

Can you not see that if your information is not clear, then we will misunderstand? Here we are thinking that this just does not happen on Ubuntu. And you are saying it does, but we are not getting all the information, are we?

By the way, amsterdamharu, As a native Englishman, I would say: "That is a bit rich, coming from you." Or, "that's rich, that is." It is a way of indicating a level of hypocrisy in the other person. I do not forget that English people are known for not speaking their own language correctly. This is why the universal language is Broken English.

Regards.

---

