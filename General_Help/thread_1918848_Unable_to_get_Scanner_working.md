---
title: "Unable to get Scanner working"
date: 2012-02-01
forum: General Help
---

### Post by Ecip on 2012-02-01
Anyone ever run into this? I'm tearing my hair out...

> ecip@Ecip:~$ brsaneconfig -a name=Scanner model=MFC-465 ip=10.0.0.111
Invalid model nameI cant get around it, no matter what it is I type for model.

I tried every variation I can think of...
> ecip@Ecip:~$ brsaneconfig -a name=Scanner model=Brother-MFC465 ip=10.0.0.111
Invalid model name
ecip@Ecip:~$ brsaneconfig -a name=Scanner model=Brother-MFC465CN ip=10.0.0.111
Invalid model name
ecip@Ecip:~$ brsaneconfig -a name=SCANNER model=BROTHER-MFC465CN ip=10.0.0.111
Invalid model name
ecip@Ecip:~$ brsaneconfig -a name=SCANNER model=MFC465CN ip=10.0.0.111
Invalid model name
ecip@Ecip:~$ brsaneconfig -a name=SCANNER model=BROTHER-MFC465CN ip=10.0.0.111
Invalid model name
ecip@Ecip:~$ brsaneconfig -a name=SCANNER model=MFC-465CN ip=10.0.0.111


---

### Post by JC Cheloven on 2012-02-01
From your post I assume you have a Brother MFC-465 scanner. 
Is it even supported by sane? Looking at [this]("http://www.sane-project.org/sane-mfgs.html#Z-BROTHER"), I don't think so...

Then, that thing 'brsaneconfig' must be a thing of a [proprietary driver]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html") from brother, isn't it?

I'm sorry, I'm not able to help with that. But at least I completed some info you should have given in the first time for someone around being actually able to help. "Better question, better answers" ;)

EDIT: perhaps [this]("http://uint32t.blogspot.com/2008/06/linux-printing-brother-mfc-465cn.html") may help you after all.

---

### Post by Ecip on 2012-02-01
I'm an idiot... I downloaded and installed brscan instead of brscan2. brscan doesnt support the 465cn.
everything now works as advertised.
sorry, everybody.

---

### Post by JC Cheloven on 2012-02-02
No worries. Glad you got it solved!

---

