---
title: "rtorrent.rc help schedule throttleing, and move on complete"
date: 2010-01-08
forum: General Help
---

### Post by markp1989 on 2010-01-08
I have added this to my rtorrent.rc and it is not affecting the download speed atal. im not sure what im doing wrong.

i want to set download speed:
150kbs between 10am and 3pm 
950kbs between  3pm and 4pm
70kbs  between  4pm and 9pm   
950kbs between  9pm and 10am


```

schedule = throttle_1,10:00:00,14:59:00,download_rate=150
schedule = throttle_2,15:00:00,15:59:00,download_rate=950
schedule = throttle_3,16:00:00,20:59:00,download_rate=70
schedule = throttle_4,21:00:00,09:59:00,download_rate=950

```



for move on complete i have added 

```
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,$d.get_custom1= ;d.set_directory=/media/torrents/finished/downloading$d.get_custom1=/media/torrents/finish$
```
 
my download folder is /media/torrents/finished/downloading and i want to move completed torrents to /media/torrents/finnished when done.

can anyone give me any pointers?

thanks Markp1989

---

