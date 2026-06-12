---
title: "RTORRENT: causing alot of disk io:"
date: 2010-01-28
forum: General Help
---

### Post by markp1989 on 2010-01-28
i have tried setting:
receive_buffer_size = 1073741824 (1gb)
send_buffer_size = 1073741824 (1gb)

i have 4gb memory 

to allow the hard drive to spin down during dowloads, but even when downloadin a 300mb file, the file isnt being downloaded to a buffer, its getting writed to the hard drive straight away, 

when monitoring iotop , i get a "disk write" for rtorrent at the speed im downloading at.

idealy i would like my hard drive to spend alot of time span down. but rtorrent is the only thing that is keeping it awake.

any rtorrent flags/settings any one can recommend me that will reduce disk io?

thanks Markp1989

---

