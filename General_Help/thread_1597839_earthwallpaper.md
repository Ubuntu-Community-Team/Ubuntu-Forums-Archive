---
title: "earthwallpaper"
date: 2010-10-15
forum: General Help
---

### Post by NIGHTHAWKward on 2010-10-15
so im trying to set up my wallpaper so that i have the live view of our planet earth that updates every 10 min or so. i got the script and i ran it through my prompt and it was saved but i dont know what i do from there to actually find it in a folder and use it. any help?

---

### Post by paulsp on 2010-10-15
Basic steps:

[LIST]
[*]Get a script to download the wallpaper (ej with wget)
[*]Set a cronjob to run this script every X minutes
[*]Set this image as your background
[/LIST]
That's it!

Sample script:

```
wget -N http://static.die.net/earth/mercator/1600.jpg -O /home/user/temp.jpg
mv /home/user/temp.jpg /home/user/mybackground.jpg
touch /home/user/mybackground.jpg #to make sure Ubuntu knows this file has changed

```

Useful link: [http://www.omgubuntu.co.uk/2010/06/quirky-wallpaper-live-earth-wallpaper/](http://www.omgubuntu.co.uk/2010/06/quirky-wallpaper-live-earth-wallpaper/)

---

### Post by NIGHTHAWKward on 2010-10-15
i got a script but i dont know how to run it through, idk what a cronjob is

---

