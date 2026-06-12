---
title: "How to make gmail defualt mail reader?"
date: 2009-11-14
forum: General Help
---

### Post by D3mon_Spawn on 2009-11-14
Hello all! I was just wondering if anyone knew how to make gmail the default mail reader in the preferred applications settings? Is it even possible??

---

### Post by XCan on 2009-11-14
I thought gmail wasn't a reader/client but merely an email service?

---

### Post by D3mon_Spawn on 2009-11-14
Yea I know, that's why I was wondering if this would work or not.

---

### Post by Rich_Roast on 2009-11-14
Why not just configure whichever your preferred email client is to connect to gmail? Gmail's help pages provide pretty comprehensive instructions about how to achieve this.

---

### Post by Giblet5 on 2009-11-14
In order for a program to be your default mail reader, you have to have that program available.

Try running "gmail" and the shell will tell you why you can't use it as the default reader (gmail: not found).

It's like asking how to make Flickr your default image viewer.

---

### Post by 73ckn797 on 2009-11-14
You can make Thunderbird receive and send email via Gmail. Do that through the account settings. I have 2 Gmail accounts plus one with my ISP. All works great.

---

### Post by D3mon_Spawn on 2009-11-14
alright...I got all this working through evolution, thanks everyone

---

### Post by markbl on 2009-11-15
> **D3mon_Spawn said:**
> alright...I got all this working through evolution, thanks everyone
I've used unix/linux mail clients for 10 years but once I started using web based gmail it just wins all over.

See the answer to your original question at [http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/)

---

### Post by cstudent on 2009-11-24
Place this in your preferred applications custom setting:

```

gnome-open https://mail.google.com/mail/?extsrc=mailto&url=%s

```

---

