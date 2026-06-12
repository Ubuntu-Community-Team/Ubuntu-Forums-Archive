---
title: "How would I post a message to the Ubuntu notification system?"
date: 2010-07-27
forum: General Help
---

### Post by Primefalcon on 2010-07-27
I am working on a calendar system for my own use, basiccaly what's doing is downloading my list of appoints from Goole calendar using GoogleCL and saving it to a text file on my computer. I am refreshing this info once every hour...

What I'd like to do is check to see if any appoints are within the next 48 hours (I know how to do this part) and if so post a message to the ubuntu notification system so it gives a little popup... How would I go about this?

---

### Post by sisco311 on 2010-07-27
```
notify-send -i path/to/icon "title" "text"
```

You may have to install **libnotify-bin**.

---

### Post by Primefalcon on 2010-07-27
> **sisco311 said:**
> ```
notify-send -i path/to/icon "title" "text"
```

You may have to install **libnotify-bin**.
Thank you very much

---

