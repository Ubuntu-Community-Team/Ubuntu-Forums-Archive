---
title: "Boxee in 64bit Natty"
date: 2011-08-15
forum: General Help
---

### Post by Purplerob on 2011-08-15
So I am trying to install boxee in natty and I have had some problems. I installed it by changing the .deb file dependencies to match the natty library (not sure what one but I found this is nothing weird and is just because a library changed slightly) When I launch it I get nothing. When I launched it from the terminal I get 
```
15/08/11 22:56:41#DEBUG#bxbgprocess.cpp:180(Start)#bg process [name=] initialized. [m_lazy=1=TRUE] -> MaxNumOfWorkingThreads was set to [2]
15/08/11 22:56:41#DEBUG#bxbgprocess.cpp:180(Start)#bg process [name=Application Messenger] initialized. [m_lazy=1=TRUE] -> MaxNumOfWorkingThreads was set to [1]
15/08/11 22:56:41#DEBUG#bxbgprocess.cpp:180(Start)#bg process [name=Http Cache CleanUp] initialized. [m_lazy=1=TRUE] -> MaxNumOfWorkingThreads was set to [1]
15/08/11 22:56:41#DEBUG#bxcurl.cpp:98(Initialize)#curl initialized. version <7.21.3>

Running Boxee test...
And the log goes to... /tmp/*myname*-boxee.log
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  161 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  27
  Current serial number in output stream:  27
X Error of failed request:  GLXBadContextTag
  Major opcode of failed request:  161 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  28
  Current serial number in output stream:  28
Boxee: asked to stop
Boxee: already stopped

```

---

### Post by Purplerob on 2011-08-16
anyone?

---

