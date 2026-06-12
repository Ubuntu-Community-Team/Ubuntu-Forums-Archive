---
title: "confused package dependencies - sensorsd"
date: 2011-03-22
forum: General Help
---

### Post by lijcam on 2011-03-22
Hi all,

I'm building a headless server with the minimal install and at them moment confused at the dependencies list for sensord package.

```
defoma fontconfig libdatrie1 libdbi0 libfontenc1 libpango1.0-0 libpango1.0-common librrd4 libthai-data libthai0 libxfont1 libxft2 ttf-dejavu ttf-dejavu-extra x-ttcidfont-conf x11-common xfonts-encodings xfonts-utils
```

My understanding sensord is merely a daemon to poll lm-sensors and to write results out to the syslog. Why would it want to install font packages and x11-common?

---

