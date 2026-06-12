---
title: "I can't burn any cd/dvd with Ubuntu 11.04"
date: 2011-07-15
forum: General Help
---

### Post by Marcelo Ramone on 2011-07-15
Hello.

I need help.

I have Ubuntu 11.04 with all updates installed.

I can not burn any cd / dvd with Braseo, GnomeBaker, nautilus burner, etc.

The discs are "apparently" normally recorded

But then Ubuntu or DVDPlayer does not recognize the DVD or CD I burned.

Conclusion: Waste DVDs because they are unusable and I can not record.

I have a Gateway nv-53 laptop.

Please Any suggestions?

P.D: In older Ubuntu editions, Fedora 15, etc, I can burn disc perfectly.

---

### Post by M1111 on 2011-07-17
I have the same problem using Brasero in Ubuntu 11.04.  I can't burn a data cd.  The burn is attempted, but the cd comes back blank and unusable.

---

### Post by deserthowler on 2011-07-17
I have the same problem.  I use k3b which usually works for me.  Worked in 11.04.  I tried to copy a couple of DVDs with no luck in Brasero then went back and copied them in k3b with no problem.  I try Brasero every time I upgrade and it never works very well but I keep hoping.  Don't know why they keep on using it.

Been that way since about 5.10 with whatever the default burner is.

Earl

---

### Post by jmszr on 2011-07-17
Marcelo Ramone,

Just a thought.

If you haven't already, you need to install through the terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

Also:

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

If you prefer to use the Software Center then you need to install: "ubuntu-restricted-extras" , "libdvdread4", and "libdvdcss2" .

From: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

+1 for K3b.

Hope that helps.

---

### Post by Marcelo Ramone on 2011-07-17
Hello,

Thanks for the replies.

I think it's my burner

Sometimes the DVDs are burned OK and sometimes fail... 

Thank you.-

---

