---
title: "Conky floating above bottom of screen"
date: 2010-03-10
forum: General Help
---

### Post by dopple on 2010-03-10
Hi. After seeing [this conky profile]("http://bigrza.deviantart.com/art/Tonky-Desktop-v0-5-135697944") I decided to try my hand at making something similar, as my conky profile looked pretty unappetising.

All my conkyrc file does at the moment, is display an image and I seem to be falling at the first hurdle. I would like the image to be flush to the bottom of the screen however it floats about 100px above the bottom of the screen. Screenshot attached and conkyrc file below. Does anyone know how to fix this?

```
use_xft yes
xftfont Liberation Sans:size=11
text_buffer_size 2048

update_interval 1
total_run_times 0

own_window yes
own_window_transparent yes
own_window_type override

double_buffer yes

minimum_size 1440 70
alignment bottom_left
TEXT
${image ~/.tonky/pix/cwb.png -s 1440x70}
```

---

### Post by dopple on 2010-03-10
Solved it. Needed the following in the conkyrc file

```
gap_x 0
gap_y 0
```

---

