---
title: "Weather Feed for Gdesklet App"
date: 2006-02-22
forum: General Help
---

### Post by AdministratorX on 2006-02-22
Hello,

I am using one of the weather applets (LTCandy ver 0.26) in Gdesklets. I live in Marietta GA, an need to get a better URL for weather feeds.

Thanks

---

### Post by PhoenixP3K on 2006-03-06
:(  I can't even get the weather desklet to work in the first place. Sorry can't help you, but at least your thread is bumped :p.

Anyone can help me out? The thing is there is two gDesklets websites and the older one has the weatherapp but why doesn't work with the newer version of gDesklets??

---

### Post by AndrewB on 2006-03-06
right click on either desktop header panel, choose "Add to panel" choose from menu. Pretty simple.

---

### Post by skirkpatrick on 2006-03-06
I'm running iWeather with no problems.

---

### Post by PhoenixP3K on 2006-03-07
I get lots of errors when I try to run it.

```

/home/phoenixp3k/.gdesklets/Displays/FTB/FTBweather.display                          
>   1 weather = get_control('IYahooWeather:b601q55ca7dpn0sbel403co51-2') 

```
```

name 'weather' is not defined                                                        
/home/phoenixp3k/.gdesklets/Displays/FTB/FTBweather.display                          
   23   Dsp.sky.value = weather.sky                                                  
   24                                                                                
   25 def icon_callback(image):                                                      
   26   Dsp.icon.uri = "gfx/weather/%s.png" % image                                  
   27                                                                                
>  28 weather.bind("city",city_callback)                                             
   29 weather.bind("status",city_callback)                                           
   30 weather.bind("temperature",data_callback)                                      
   31 weather.bind("sky",data_callback)                                              
   32 weather.bind("icon",icon_callback)                                             
   33                                                                                
   34  

```
```

name 'weather' is not defined                                                        
<internal>                                                                           
>   1 __retrieve__ = weather.city                  

```

```
name 'weather' is not defined                                                        
<internal>                                                                           
>   1 __retrieve__ = weather.country      
```

And it goes on for some time... is there some package I might be missing? I looked for weather in Synaptic and only found several dockapp. I've posted the codes apart because when I close the warning screen the next pops.

---

### Post by Xian on 2006-03-07
You should have better luck with [GoodWeather](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=204).
Or you could try adesklets...

---

### Post by Leigh on 2006-03-07
Getting back to the original thread, what is wrong with the weather display you are using. I installed LTcandy as a test and entered "Marietta" for the city and "United States" for the Country and it worked. I also entered the Yahoo weather URL for Marietta adn that gave the same result.

What problems, if any, are you experiencing?

BTW, the URL I used is: [http://weather.yahoo.com/forecast/USGA0353_f.html](http://weather.yahoo.com/forecast/USGA0353_f.html)

---

### Post by justinjstark on 2006-03-07
Please note that the gdesklets-data package includes many many deprecated desklets.  You see, the folks programming gdesklets-core keep changing the way that desklets work (they used to use sensors, now controls etc).  Whoever put together the gdesklets-data package without checking for desklets compatibility with the stable version of gdesklets has caused lots of people to email me about desklets that I removed from gdesklets.gnomedesktop.org long ago wondering why they don't work.

Solution: Somebody needs to fix the gdesklets-data package and remove old desklets that throw errors.  I may do this one of these days if I have some time and try to get it in the repositories.

---

### Post by PhoenixP3K on 2006-03-08
Well GoodWeather is working, it's a good desklet. Thank you. I'll look and compare to adesklets.

---

### Post by skirkpatrick on 2006-03-09
[QUOTE=blaksaga]Please note that the gdesklets-data package includes many many deprecated desklets.  You see, the folks programming gdesklets-core keep changing the way that desklets work (they used to use sensors, now controls etc).  Whoever put together the gdesklets-data package without checking for desklets compatibility with the stable version of gdesklets has caused lots of people to email me about desklets that I removed from gdesklets.gnomedesktop.org long ago wondering why they don't work.

Solution: Somebody needs to fix the gdesklets-data package and remove old desklets that throw errors.  I may do this one of these days if I have some time and try to get it in the repositories.[/QUOTE]

Blaksaga, is there a possibility that the version of gdesklets that is built in the repositories (0.35.2) that has the problem with the percentage bars in the desklets has been fixed in a newer release?  I'm not sure if you've seen the other threads but the percentage bars all show 100% on all of the desklets.

---

### Post by justinjstark on 2006-03-09
[QUOTE=skirkpatrick]Blaksaga, is there a possibility that the version of gdesklets that is built in the repositories (0.35.2) that has the problem with the percentage bars in the desklets has been fixed in a newer release?  I'm not sure if you've seen the other threads but the percentage bars all show 100% on all of the desklets.[/QUOTE]

[quote=gdesklets.org]gDesklets 0.35.3
Released on 15.01.2006
This release fixes some issues concerning GTK 2.8.

ChangeLog
    * Implemented workaround to make gauges work with GTK 2.8[/quote]

I'm sure that you can find a .deb file of 0.35.3 to install if you google.

---

### Post by skirkpatrick on 2006-03-09
Thanks, I'll look around!

---

