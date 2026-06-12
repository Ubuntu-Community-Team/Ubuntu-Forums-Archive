---
title: "shell script"
date: 2009-06-29
forum: General Help
---

### Post by FFGANDALF on 2009-06-29
I wish to write a shell script that will run as part of cron. As part of the script I want to check if a certain website is currently up on Firefox. I've been unable to find where firefox stores this information using grep and any help would be appreciated.

---

### Post by t4thfavor on 2009-06-29
I believe that the information is not stored until firefox is closed, and saved. It may not be possibe to load that information from an outside process, this could be intentional due to the browsers security model. I would check the mozilla site and see if you can find anything about programmati access to site information.

---

### Post by ghostdog74 on 2009-06-29
what is it exactly you are wanting to do?? i don't see a use for this.

---

### Post by t4thfavor on 2009-06-29
He wants to execute a shell script that accesses an instance of FireFox to see if a certain site is active in the browser window. Kinda like if you had a kiosk you would want to know if your app was still running or not.

---

### Post by ghostdog74 on 2009-06-30
```

lsof |awk '/firefox/ && /ESTABLISHED/'

```

---

### Post by FFGANDALF on 2009-06-30
thanks, the site that I actually want to cheeck for is listed (pandora) but the others are to sites that don't exist?

firefox   17133     USERNAME   54u     IPv4     737545               TCP USERNAME-laptop.local:56239->vw-in-f101.google.com:www (ESTABLISHED)
firefox   17133     USERNAME   65u     IPv4     738980               TCP USERNAME-laptop.local:39187->[www.pandora.com:www](www.pandora.com:www) (ESTABLISHED)
firefox   17133     USERNAME   67u     IPv4     738984               TCP USERNAME-laptop.local:39188->[www.pandora.com:www](www.pandora.com:www) (ESTABLISHED)
firefox   17133     USERNAME   68u     IPv4     738986               TCP USERNAME-laptop.local:39189->[www.pandora.com:www](www.pandora.com:www) (ESTABLISHED)
firefox   17133     USERNAME   69u     IPv4     739145               TCP USERNAME-laptop.local:41040->[www.pandora.com:www](www.pandora.com:www) (ESTABLISHED)
firefox   17133     USERNAME   71u     IPv4     739149               TCP USERNAME-laptop.local:38770->autocomplete.pandora.com:www (ESTABLISHED)
firefox   17133     USERNAME   72u     IPv4     739009               TCP USERNAME-laptop.local:55292->q-138.n-81.18.240.qore.nl:www (ESTABLISHED)
firefox   17133     USERNAME   73u     IPv4     739156               TCP USERNAME-laptop.local:41043->[www.pandora.com:www](www.pandora.com:www) (ESTABLISHED)
firefox   17133     USERNAME   74u     IPv4     737455               TCP USERNAME-laptop.local:54428->qw-in-f100.google.com:www (ESTABLISHED)
firefox   17133     USERNAME   75u     IPv4     739157               TCP USERNAME-laptop.local:41044->[www.pandora.com:www](www.pandora.com:www) (ESTABLISHED)
firefox   17133     USERNAME   76u     IPv4     739170               TCP USERNAME-laptop.local:39203->[www.pandora.com:www](www.pandora.com:www) (ESTABLISHED)
firefox   17133     USERNAME   83r     IPv4     739274               TCP USERNAME-laptop.local:40969->209-18-36-32.tbone.rr.com:www (ESTABLISHED)

---

### Post by ghostdog74 on 2009-06-30
no they do exist. At the backend, firefox may be connecting to other sites, such as for updates, or some of your extensions and plugins etc....

---

### Post by FFGANDALF on 2009-07-05
thanks although after playing around I think that it is easier to use lsof | grep -e "WEBSITE" then the awk method but that is just b/c I actually understand how to use grep.

---

