---
title: "KDevelop 4 not downloading"
date: 2011-04-19
forum: General Help
---

### Post by postmodernism on 2011-04-19
Hello everyone, I have tried to download KDevelop4 on two machines (at home and work), using both the normal Ubuntu Software Center and the Package Manager. Both times, it says it failed to download. I have never experienced a problem with this.

Here is the output when using the package manager:
```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.5.1-0ubuntu8_all.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdecore5_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkpty4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdesu5_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdeui5_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdnssd4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libnepomuk4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libsolid4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkio5_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkfile4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkjsapi4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkparts4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libktexteditor4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkhtml5_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkmediaplayer4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libknewstuff3-4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libknotifyconfig4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkutils4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libnepomukquery4a_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdewebkit5_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libthreadweaver4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libplasma3_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkatepartinterfaces4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkjsembed4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkntlm4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkrosscore4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkrossui4_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdoctools_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs-bin_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-plugins_4.5.1-0ubuntu8_amd64.deb
  404  Not Found [IP: 91.189.88.45 80]



```

Are the files just missing from the repository?

---

