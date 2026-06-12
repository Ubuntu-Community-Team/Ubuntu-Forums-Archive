---
title: "Mounting a network share to prompt for password"
date: 2011-04-30
forum: General Help
---

### Post by morrty11 on 2011-04-30
I was wondering if there is a way to mount a network CIFS share manually to allow it to prompt for password.

I've been Googling around and found a couple options. One was to store your credentials in a file and then add the fstab entry to look at the file. I'm not particularly fond of the idea of storing my credentials in a plain text file though, even if I put file permissions on it.

Is there a way to mount the share so that it prompts for credentials. The share isn't always online so I want to mount it manually.

Thanks.

---

### Post by morrty11 on 2011-05-01
b

---

### Post by morrty11 on 2011-05-02
b

---

### Post by Morbius1 on 2011-05-02
I guess I don't understand the question since this is the way it works normally.

If you go to Nautilus > Network and click on the remote share it will ask you for credentials. 

The only thing I can think of is that you may not know that it does mount the remote share in a somewhat inconvenient location:
> /home/your-user-name/.gvfsIt's in a hidden folder as you can see so you need to enable "show hidden files" in Nautilus to see it.

Am I missing something in your question?

---

### Post by morrty11 on 2011-05-03
Oh sorry, I'm running 10.04 Server. I do not have a GUI.

---

### Post by morrty11 on 2011-05-03
I should clarify a bit.

I've created a folder where I want to mount this share:
```

mkdir /media/share

```

I've added an entry into my /etc/fstab file:
```

//network/share /media/share cifs user,uid=admin,gid=users,rw,suid,credentials=/etc/credspwd 00

```

I created the credspwd file:
```

touch /etc/credspwd
echo username=admin > /etc/credspwd
echo password=password > /etc/credspwd

```

This was the instructions given to me but I don't like the fact that my password is stored in plain text in that file. Can I get this to prompt me for password when I mount it?

---

### Post by morrty11 on 2011-05-03
I've solved this issue.

Apparently I can just do the following:
```

sudo mount //server/share /media/share -o username=admin

```

and then it prompts me for the password.

---

