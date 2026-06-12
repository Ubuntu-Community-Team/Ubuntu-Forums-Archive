---
title: "IM's not working!"
date: 2012-03-04
forum: General Help
---

### Post by litmux on 2012-03-04
hey there, all of a sudden all instant messaging application stopped working, I tried different application still wont work. I even tried using different pcs, on my laptop it has ubuntu 10.10 and desktop 11.10 both wont work. It keeps telling me "Connecting..." and it stays like that but it wouldn't open and wouldn't show me the contact list it keeps on connecting. It used to work fine, Iit has been doing that for like about more than 3 months.

---

### Post by Sonsum on 2012-03-04
> **litmux said:**
> hey there, all of a sudden all instant messaging application stopped working, I tried different application still wont work. I even tried using different pcs, on my laptop it has ubuntu 10.10 and desktop 11.10 both wont work. It keeps telling me "Connecting..." and it stays like that but it wouldn't open and wouldn't show me the contact list it keeps on connecting. It used to work fine, Iit has been doing that for like about more than 3 months.

What IM protocol are you using? (AIM? Facebook? GTalk? Other?)

---

### Post by litmux on 2012-03-05
I'm using MSN but I even tried to work on IRC doesn't work as well..

---

### Post by Sonsum on 2012-03-05
Have you tried this on a different internet connection? That sounds like the only common denominator in this situation.

---

### Post by litmux on 2012-03-06
Yup I tried it through different ISPs, I thought maybe something is blocked but didnt work...
also I had a problem with ubuntu updates but then I fixed it by changing my country sever into the main server and it worked, dunno if this is related...

---

### Post by Script Warlock on 2012-03-06
> **Maillard965 said:**
> <snip>It used to work fine, Iit has been doing that for like about more than 3 months. check your msn account [here]("https://imo.im/") if it's working or check [here]("http://askubuntu.com/questions/76948/problems-connecting-msn-with-empathy")

---

### Post by HiImTye on 2012-03-06
```
sudo apt-get remove telepathy-butterfly
```
remove and then re-add your MSN account

should work fine after that

---

### Post by litmux on 2012-03-10
Thanks Worked =)

---

