---
title: "logrotate problems"
date: 2012-05-11
forum: General Help
---

### Post by Godsbrother on 2012-05-11
Hi,

Im looking for some help with logrotate. I am trying to setup logs to rotate daily and when they reach 1g in size. The logs contain web traffic info from a loadbalancer.

the conf file from /etc/logrotate.d/zxtm is below. I getting odd things happening but essentially the compression isnt working and I dont think the size trigger is either.

Any help appreciated.



/usr/local/zeus/zxtm/log/VServers/IW/* /usr/local/zeus/zxtm/log/VServers/CC/* {
daily
size=1024M 
compress 
delaycompress
}
/usr/local/zeus/admin/log/errors /usr/local/zeus/zxtm/log/errors { 
weekly
rotate 5 
compress
delaycompress
}

---

### Post by cmont899 on 2012-05-11
You don't need the = on you size setting, try:

```
size 1024M
```

See if that alleviates the other issues you are seeing.

---

### Post by SeijiSensei on 2012-05-11
You can test the configuration by running

```
sudo logrotate -v -f /etc/logrotate.d/zxtm
```

That should either flag errors or run the rotation immediately.

---

### Post by Godsbrother on 2012-05-21
Ok so it rotating .. sort of.

It doesnt seem to be gz'ing the files althopugh it did when I ran it from the command line once. I am also getting lots of empty file named xxx.log.1.1.1.1 with differneing numbers of .1 on the end.

Very confused now.

file currently looks like this.

/usr/local/zeus/zxtm/log/VServers/IW/ /usr/local/zeus/zxtm/log/VServers/CC/* {
daily
rotate 28
size 1024M 
compress 
delaycompress
}
/usr/local/zeus/admin/log/ /usr/local/zeus/zxtm/log/ { 
weekly
rotate 5 
compress
delaycompress
}

---

