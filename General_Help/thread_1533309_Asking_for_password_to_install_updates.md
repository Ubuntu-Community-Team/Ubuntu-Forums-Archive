---
title: "Asking for password to install updates?"
date: 2010-07-17
forum: General Help
---

### Post by Zundap on 2010-07-17
Hi everyone, could any one please help, i am trying to update the Ubuntu , but when i click to install the updates, i get asked for a password, but i don't remember using a password option when installing Ubuntu. Is there a way around this problem?  Thanks.

---

### Post by lisati on 2010-07-17
Asking for a password to do administrative stuff is normal and is done to help protect your system. Using the same password you'd use to log in to Ubuntu is the normal response.

---

### Post by SnickerSnack on 2010-07-17
> **Zundap said:**
> Hi everyone, could any one please help, i am trying to update the Ubuntu , but when i click to install the updates, i get asked for a password, but i don't remember using a password option when installing Ubuntu. Is there a way around this problem?  Thanks.

Have you tried googling for it?  The first three links I got from trying "override password ubuntu" looked promising.  One of them was for psychocats.net (which usually explains things very well).

---

### Post by capscrew on 2010-07-17
> **Zundap said:**
> Hi everyone, could any one please help, i am trying to update the Ubuntu , but when i click to install the updates, i get asked for a password, but i don't remember using a password option when installing Ubuntu. Is there a way around this problem?  Thanks.

The updates must be done as **root **and therefore **sudo ** must be invoked.  The script running the GUI interface you are using is doing just that.  The first account you made is a member of sudoers.  It is asking for that account password.

See [**_here _**]("https://help.ubuntu.com/community/RootSudo")for sudo.

---

### Post by lisati on 2010-07-17
> **SnickerSnack said:**
> Have you tried googling for it?  The first three links I got from trying "override password ubuntu" looked promising.  One of them was for psychocats.net (which usually explains things very well).

I'd advise against overriding the administrative password, otherwise you could leave your system more vulnerable to attack e.g. malware.

---

### Post by SnickerSnack on 2010-07-17
> **lisati said:**
> I'd advise against overriding the administrative password, otherwise you could leave your system more vulnerable to attack e.g. malware.

That's not what I meant.  The pyschocats article shows how to reset user passwords without knowing a user password.  I was guessing that the OP had automatic login setup, and therefore didn't remember his password.

---

### Post by lisati on 2010-07-17
> **SnickerSnack said:**
> That's not what I meant.  The pyschocats article shows how to reset user passwords without knowing a user password.  I was guessing that the OP had automatic login setup, and therefore didn't remember his password.

Thank you for clarifying.

---

### Post by Zundap on 2010-07-17
> Have you tried googling for it? The first three links I got from trying "override password ubuntu" looked promising. One of them was for psychocats.net (which usually explains things very well).
 

 I have tried the psycocats.net advice but when I type ls home, I get the message: ls cannot access home no such file or dierctory. So io am still in the same position of not being able to install my updates.  
 

 Any more advise would be greatly apreciated, thanks  
 

> [capscrew said as below]("http://ubuntuforums.org/member.php?u=722119")
 The updates must be done as **root **and therefore **sudo **must be invoked. The script running the GUI interface you are using is doing just that. The first account you made is a member of sudoers. It is asking for that account password.


 But I have never joined sudoers, so I dont have a password., any more advise would be most welcome, thanks.

---

### Post by mike555 on 2010-07-17
did someone else install Ubuntu for you? who ever installed Ubuntu had to put in a password or it would not install ......... if you don't know it or who ever installed Ubuntu can't remember then you will need to reset it ...

 unless your just a guest with limited account , in which case you will need to ask the admin.

---

### Post by WorMzy on 2010-07-17
If you didn't set a password for your own account, then try just pressing Enter at the password prompt. If that doesn't work, try generic passwords like "password" and "ubuntu".

---

### Post by Zundap on 2010-07-17
> **mike555 said:**
> did someone else install Ubuntu for you? who ever installed Ubuntu had to put in a password or it would not install ......... if you don't know it or who ever installed Ubuntu can't remember then you will need to reset it ...

 unless your just a guest with limited account , in which case you will need to ask the admin.

No i installed it my self and it did not ask for a password, thanks for the reply.

---

### Post by louieb on 2010-07-17
> **Zundap said:**
> I have tried the psycocats but when I type ls home, I get the message: ...

You need follow the directions exactly its not ls home its:
```
ls /home
```Hang in there you'll get it.

> No i installed it my self and it did not ask for a password, thanks for  the reply.

Thats weird - the installer should have ask you to type it in twice.

---

### Post by Zundap on 2010-07-19
I have sorted the problem, i found a password that i did not recognise, i tried it and it worked, so please forgive me for wasting your time. By way of explanation, i am an old guy and my memory is failing me badly, its some thing i have to live with i am afraid.


louieb was right that i had written the code wrongly, but even when i put it in as it should be it still did not work.
 

 So I apologies for wasting your time and a big thanks to all of you who tried to help me, you will probably never know how good it made me feel to know that there are so many lovely people around the world who are wiling to help others like my self who are so far behind in technical matters.  
 

 Thanks again to all of of your guys.

---

### Post by WorMzy on 2010-07-19
Don't worry about wasting our time, we're all here because we're happy to help; all that matters to us is that your problem gets resolved, which, I'm glad to hear, you managed to do. :)

Good luck in the future, and please don't hesitate to ask for assistance if you run into another problem.

---

### Post by Rubi1200 on 2010-07-19
Glad you sorted it out!

---

### Post by etdsbastar on 2010-07-19
> **Rubi1200 said:**
> Exactly!

You **cannot**, I repeat it is **impossible**, to install Ubuntu **without** creating a user account **with** a password (the minimum the installer will accept is 4 character if I am not mistaken).

Sorry for the emphasis, but this is not the first post I have read from someone claiming they never created an account with password.

I have tested this myself and the installer will not allow it.

I think mike555 has hit the nail on the head.

You are absolutely right ruby, I totally agree with you, because no-one ever till now created an user without a password during installation of Ubuntu.

---

### Post by etdsbastar on 2010-07-19
> **Zundap said:**
> Hi everyone, could any one please help, i am trying to update the Ubuntu , but when i click to install the updates, i get asked for a password, but i don't remember using a password option when installing Ubuntu. Is there a way around this problem?  Thanks.

Better you should say, you have forgotten your password what you have given while installing Ubuntu. So that we can support you in a much better way.

---

### Post by Rubi1200 on 2010-07-19
I edited my original post because after I submitted it I saw the response from the OP and did not wish to appear insensitive to his situation.

---

### Post by etdsbastar on 2010-07-19
> **Rubi1200 said:**
> I edited my original post because after I submitted it I saw the response from the OP and did not wish to appear insensitive to his situation. But the fact is I have read posts from people claiming not to have created a password.

Thanks a lot for changing your original post and I am sorry if i had hurted you in any way. That was not my intension, I actually wanted you to be clear in the forums so that we can help you accordingly and with true intensions.

Take care.

---

### Post by capscrew on 2010-07-19
> **etdsbastar said:**
> Better you should say, you have forgotten your password what you have given while installing Ubuntu. So that we can support you in a much better way.

The OP did state the he had forgotten it: when he realized it!  It sure is easy to second guess when you know all the facts.

Late comers should always read the COMPLETE thread.

---

### Post by etdsbastar on 2010-07-19
> **capscrew said:**
> The OP did state the he had forgotten it: when he realized it!  It sure is easy to second guess when you know all the facts.

Late comers should always read the COMPLETE thread.


Thanks capscrew.... 

But this is what I posted before...
> Thanks a lot for changing your original post and I am sorry if i had  hurted you in any way. That was not my intension, I actually wanted you  to be clear in the forums so that we can help you accordingly and with  true intensions.


I hope you have read this too...

---

### Post by capscrew on 2010-07-19
> **etdsbastar said:**
> Thanks capscrew.... 

But this is what I posted before...


I hope you have read this too...

Of course I did.  If you were so interested doing the right thing, you would have edited you post rather than added a second post that does not refer to the first.

To me that would have been the appropriate thing to do, as @Rubi1200 did with his post.

Edit: As this is off topic I will stop here. No more comments.

---

### Post by etdsbastar on 2010-07-19
> **capscrew said:**
> Of course I did.  If you were so interested doing the right thing, you would have edited you post rather than added a second post that does not refer to the first.

To me that would have been the appropriate thing to do, as @Rubi1200 did with his post.

Edit: As this is off topic I will stop here. No more comments.

Ok, I agree with you dont take it otherwise please, but i would like to explain you heartily that at that time there was some net problems while submitting my post that's why dual posting happened.

Anyways, sorry if i hurted you in anyway.

---

