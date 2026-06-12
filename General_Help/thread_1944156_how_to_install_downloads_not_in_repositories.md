---
title: "how to install downloads not in repositories"
date: 2012-03-20
forum: General Help
---

### Post by hwally on 2012-03-20
I downloaded cudatoolkit_4.1.28_linux_32_ubuntu10.04.run.  It wasn't in any repositories.  I searched but only found info on how to install packages from repositories.  The download is in my root folder.  Thank you for your attention

---

### Post by PhantomTurtle on 2012-03-20
You have to make it executable first. To do this open terminal, and navigate to where the file is using,

```
cd
```
then make it executable using,
```
sudo chmod +x filename.run
```
then just run it by typing the filename
```
./filename.run
```

EDIT - If when you run ./filename and it gives you a message saying 'permission denied' then add "sudo" in front of it.

---

### Post by hwally on 2012-03-20
Thank you very much for the quick and helpful reply.  It installed without a hitch.  You made my day,

---

### Post by PhantomTurtle on 2012-03-20
No Problem. You should mark this thread as solved.

---

### Post by hwally on 2012-03-20
Ok, I'm trying to add cuda toolkit to pyrit.  When it comes time to add it I'm told to download and install cudatoolkit then type in sh cudatoolkit_4.1.28_linux_32_ubuntu10.04.run  I hit enter and get the message that cudatoolkit (rest of the file): no such file or directory.  any ideas or suggestions?   Thanks again

---

### Post by hwally on 2012-03-20
I reran the commands you sent and at the end it says:Enter install path (default /usr/local/cuda, '/cuda' will be appended):  I just hit enter before.  Is there another command I should have entered?

---

### Post by PhantomTurtle on 2012-03-21
> **hwally said:**
> I reran the commands you sent and at the end it says:Enter install path (default /usr/local/cuda, '/cuda' will be appended):  I just hit enter before.  Is there another command I should have entered?

Does that mean you reinstalled the package? What happened after you hit enter?

---

