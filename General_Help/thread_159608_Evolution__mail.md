---
title: "Evolution  mail"
date: 2006-04-13
forum: General Help
---

### Post by gos1 on 2006-04-13
Do you know any other software like evolution. I am getting some problems at evolution and want try another one. Or solve it  
 ---------
 evolution problem :
 MAIL FROM command failed: Must issue a STARTTLS command first f16sm1462391qba
----------------
Do you know when does it happens ?

---

### Post by niviche on 2006-04-13
Kontact is the closest equivalent. It is a KDE app, but also contains an email part, a calendar part, and so on and so forth.

If you are after an email software only, you can try Thunderbird.

---

### Post by dcstar on 2006-04-13
[QUOTE=gos1]Do you know any other software like evolution. I am getting some problems at evolution and want try another one. Or solve it  
 ---------
 evolution problem :
 MAIL FROM command failed: Must issue a STARTTLS command first f16sm1462391qba
----------------
Do you know when does it happens ?[/QUOTE]
Looks like you aren't using the correct authentication for the particular e-mail account you are using.

Go into the Preferences for that account and use the "Check supported types" function (for sending as well as receiving) and see if you have a list of authentication methods offered to you.

Some e-mail clients will automatically pick one out and use it, Evolution seems to want you to know what is available and have you specifically choose one.

---

### Post by perdubug on 2007-12-26
I also met this problem on my Ubuntu 7.10+Evolution 2.12.2. But it works finally after setting SMTP stuff like below:
**Server Type**:SMTP
**Server**:smtp.gmail.com:465
**Server Requests authentication**: yes
**User Secure Connection**:SSL
**Type**:PLAIN
**Username**: <your mail address>@gmail.com

---

### Post by psusi on 2007-12-26
I use Mozilla Thunderbird.

---

### Post by Ulir on 2008-01-03
> **perdubug said:**
> I also met this problem on my Ubuntu 7.10+Evolution 2.12.2. But it works finally after setting SMTP stuff like below:
**Server Type**:SMTP
**Server**:smtp.gmail.com:465
**Server Requests authentication**: yes
**User Secure Connection**:SSL
**Type**:PLAIN
**Username**: <your mail address>@gmail.com

[COLOR="Red"]Thank you very much[/COLOR] :popcorn:

[COLOR="Blue"]Evolution 2.12.1 on Ubuntu Desktop 7.10.[/COLOR]

---

### Post by vijaychn on 2008-01-12
I am not sure if you resolved this issue. But I did. All you have to do is select SSL encryption in the "Sending Email" tab of the preferences.


Good luck

Vijay

---

### Post by fulgencio on 2008-01-24
I used the faq on:[http://www.go-evolution.org/FAQ#How_can_I_access_my_GMail_POP_account.3F]("http://www.go-evolution.org/FAQ#How_can_I_access_my_GMail_POP_account.3F")
but that didn't work: so I changed the following:

[B]Server:smtp.gmail.com:465

User Secure Connection:SSL[/B]

leaving the rest as the faq recommends 
after that it worked beautifully

---

