---
title: "can't uninstall zend studio"
date: 2010-03-23
forum: General Help
---

### Post by unpresedented on 2010-03-23
dear all,
I navigated to usr/local/zend/zendstudio-7_1_2/uninstallzendstudio folder and there are some files, one of them is uninstallzendstudio i double clicked it, and chose RUN .. but it gives me error : you do not have sufficent privileges to perform uninstallation, fix the problem ...

what should i do although I'm the administrator on the machine ...

---

### Post by unpresedented on 2010-03-23
no help :( ?

---

### Post by unpresedented on 2010-03-23
I have uninstalled it after changing permission to that file (something like sudo chmod x) ..

---

### Post by simplysimple on 2010-07-07
Open up a terminal.

Navigate to the Uninstall folder for Zend Studio. On my machine it was located at: /usr/local/Zend/ZendStudio-7.2.0/Uninstall Zend Studio - 7.2.0

Type the following in the terminal:
```
cd /usr/local/Zend/ZendStudio-7.2.0\Uninstall\ Zend\ Studio\ -\ 7.2.0/

```

Now that you are in the Uninstall directory, type in the following in the terminal:
```
sudo sh ./Uninstall_Zend_Studio_-_7.2.0
```

This should start the uninstall program. 

Note: You will need to adjust the above to match your version of Zend Studio.

---

### Post by johansyd on 2012-01-29
This uninstall folder doesn't exist anymore.

---

