---
title: "htdocs sym link"
date: 2010-06-02
forum: General Help
---

### Post by ShizzlePDX503 on 2010-06-02
so I installed the current version of XAMPP in /opt and I want to use htdocs that is in my home directory /home/user/htdocs since I have permission to read/write and I don't have those permissions in /opt/lampp/htdocs

is this correct?  ```
ln -s /opt/lampp/htdocs /home/user/htdocs
```

or is it the other way around?
```
ln -s /home/user/htdocs /opt/lampp/htdocs
```

Thanks

---

### Post by ShizzlePDX503 on 2010-06-02
actually I tried both ways and I still don't have permission to add to the link

---

