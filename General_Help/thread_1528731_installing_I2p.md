---
title: "installing I2p"
date: 2010-07-11
forum: General Help
---

### Post by hihihi100 on 2010-07-11
Hi there:

Im following the instructions that can be found at: [https://help.ubuntu.com/community/I2P](https://help.ubuntu.com/community/I2P)

Im stucked in this step:

```
java -jar i2pinstall-x.x.x.exe
Unable to access jarfile i2pinstall-x.x.x.exe

```

Please confirm if this happens because I am not in the right folder (in my case, I downloaded i2pinstall_0.7.14 to the "downloads" folder)

If so, please consider that Im a noob, and I would really appreciate if any user would write exactly what Do I have to type in the terminal to end the installation of the file

thanks

---

### Post by lykeion on 2010-07-11
You can try to make the file executable like this:```
chmod u+x i2pinstall_0.7.14.exe
```Then run it like this: ```
java -jar i2pinstall_0.7.14.exe
```Hope that it helps (and if so make sure to mark this thread as SOLVED to let others easily find a solution)

---

