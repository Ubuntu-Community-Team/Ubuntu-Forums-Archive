---
title: "Finding a specific file in Ubuntu"
date: 2011-05-14
forum: General Help
---

### Post by Wuxin on 2011-05-14
[FONT=Times New Roman][SIZE=3]I want to know where to find a specific file in Ubuntu.  I have the file name but I don't know where to place it to bring up the appropriate file.  Does anyone have a suggestion?  Thank you in advance![/SIZE][/FONT]

---

### Post by Duncan Williams on 2011-05-14
In natty just type it in the dash (top left icon).

---

### Post by Wuxin on 2011-05-14
[FONT=Times New Roman][SIZE=3]I'm still using Ubuntu 10.10.  [/SIZE][/FONT]

---

### Post by Rubi1200 on 2011-05-14
Places > Search for Files

By default it looks in the home directory but you can set it to look in other locations as well.

---

### Post by Wuxin on 2011-05-14
[FONT=Times New Roman][SIZE=3]Let me be more specific: this is the file I want to be able to see:

[/SIZE][/FONT]/var/BACKUPS/2011-05-06_21:55:37_rsync.log

[FONT=Times New Roman][SIZE=3]I tried "Search for Files" but it comes up with nothing.  
I think this has to be recovered in a terminal, no?  
[/SIZE][/FONT]

---

### Post by 5149.5 on 2011-05-14
Your question isn't specific. "Bring up" and "see" a file don't really mean anything. Do you want to view it's contents?

```
cat /var/BACKUPS/2011-05-06_21:55:37_rsync.log | less 
```

---

### Post by Wuxin on 2011-05-14
[FONT=Times New Roman][SIZE=3]Yes, that's it--I want to view its content.  I believe this has to done through a terminal, no?[/SIZE][/FONT]

---

### Post by TeoBigusGeekus on 2011-05-14
> **Wuxin said:**
> [FONT=Times New Roman][SIZE=3]Yes, that's it--I want to view its content.  I believe this has to done through a terminal, no?[/SIZE][/FONT]

Yes.

---

### Post by 5149.5 on 2011-05-14
> **Wuxin said:**
> [FONT=Times New Roman][SIZE=3]Yes, that's it--I want to view its content.  I believe this has to done through a terminal, no?[/SIZE][/FONT]

Yes. If you paste that command into a terminal, you can view the contents of the file.

---

### Post by m_duck on 2011-05-14
> **5149.5 said:**
> Your question isn't specific. "Bring up" and "see" a file don't really mean anything. Do you want to view it's contents?

```
cat /var/BACKUPS/2011-05-06_21:55:37_rsync.log | less 
```

Cat *and* less? :p

```
less /var/BACKUPS/2011-05-06_21:55:37_rsync.log
```

---

### Post by TeoBigusGeekus on 2011-05-14
> **m_duck said:**
> cat *and* less? :p

```
less /var/backups/2011-05-06_21:55:37_rsync.log
```

dope!!!!!!

---

### Post by 5149.5 on 2011-05-14
> **m_duck said:**
> Cat *and* less? :p

```
less /var/BACKUPS/2011-05-06_21:55:37_rsync.log
```

I thought about that but left it the way it was so that he learned two commands instead of one and he learned how to connect commands. It was three lessons in one.:)

---

