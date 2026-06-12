---
title: "Nautilus and ftp"
date: 2006-03-19
forum: General Help
---

### Post by tedius on 2006-03-19
I'm trying to launce Nautilus from a script so that it will log me into an ftp site, the problem is that there is a "@" in my user name. 
eg```
user@hostname.com
```
So my coomand looks like this;
```
nautilus ftp://user@hostname.com:password@ftp.hostname.com
```
But I get the following error;
```
Nautilus cannot display "ftp:".
```
Does any know if what I'm trying is posible and if so what am I doing wrong?

Thanks

---

### Post by iramhernandez on 2006-03-19
Just a guess here since I don't have an account to test this on.  But you could try:
```
 nautilus ftp://"user@hostname.com":password@ftp.hostname.com
```

or

```
 nautilus ftp://user\@hostname.com:password@ftp.hostname.com
```

---

### Post by tedius on 2006-03-19
Thanks for the suggestions, but I have tried them both and neither of them work

---

