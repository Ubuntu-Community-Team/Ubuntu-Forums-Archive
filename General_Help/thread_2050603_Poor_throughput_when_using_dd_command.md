---
title: "Poor throughput when using dd command"
date: 2012-08-31
forum: General Help
---

### Post by aef54 on 2012-08-31
When I use the following command to overwrite a drive with zeros:

[COLOR=Red]###Warning: command designed to irrecoverably destroy data###[/COLOR]
```

sudo dd if=/dev/zero of=/dev/sda
```I get a throughput of about 20MB/s. My HDD should be able to write with a maximum speed of 100MB/s

Why is the writing speed so much lower? Is there a way to increase the throughput (writing speed)?

Kind regards,
aef

---

### Post by aef54 on 2012-08-31
Small bump. Somebody's gotta know this answer.

Generating zeros can't be a hard task for the CPU and if the disk is able to write at higher speeds, why doesn't it?

---

### Post by steeldriver on 2012-08-31
maybe the default bs is not optimal for the write buffer? have you tried different block sizes?

[http://unix.stackexchange.com/questions/9432/is-there-a-way-to-determine-the-optimal-value-for-the-bs-parameter-to-dd](http://unix.stackexchange.com/questions/9432/is-there-a-way-to-determine-the-optimal-value-for-the-bs-parameter-to-dd)

---

### Post by dodo3773 on 2012-08-31
Yeah the default block size is your issue. It takes forever that way. You should be fine at a megabyte at least.

---

### Post by aef54 on 2012-08-31
Thanks guys. That worked. I changed the blocksize to 1MB. 

I used this command:
[COLOR=Red]###Warning: command designed to irrecoverably destroy data###[/COLOR]

```

sudo dd if=/dev/zero of=/dev/sda bs=1M
```
Now I got a much greater speed, an average of 92 MB/s


Thanks again. I appreciate it.

---

