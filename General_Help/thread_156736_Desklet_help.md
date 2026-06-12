---
title: "Desklet help"
date: 2006-04-07
forum: General Help
---

### Post by truNWA on 2006-04-07
When i get desklets, almost all of them come up with errors. It may just be that i have bad desklets, but i don't think so.... anyway I tried Flickr Frame and i comes up with this error:

```
list index out of range                                                              
/home/johnathan/.gdesklets/Displays/FlickrFrame/flickrframe.display                  
   15     timer_changed=True                                                         
   16                                                                                
   17 def new_image():                                                               
   18    if(fl_tag != ""):                                                           
   19      img_ctrl.tags=fl_tag                                                      
>  20      Dsp.fl_image.uri=img_ctrl.imageurlbytag                                   
   21    elif(fl_user != ""):                                                        
   22      img_ctrl.user=fl_user                                                     
   23      Dsp.fl_image.uri=img_ctrl.imageurlbyuser                                  
   24    return True                                                                 
   25                                                                                
   26 def new_timer():                                                               

```

If anyone knows of anywhere to get some good desklets, please post the link.

---

### Post by taurus on 2006-04-07
I assume you are talking about gdesklets.  Well, there is only one place you can get whatever you want and it's at [http://gdesklets.gnomedesktop.org/categories.php](http://gdesklets.gnomedesktop.org/categories.php).  So, head over there and help yourself with whatever you need...

---

### Post by truNWA on 2006-04-07
any thoguhts on the error i'm getting?

---

### Post by taurus on 2006-04-07
Not sure and I am not a real good python programmer so I will pass on figuring out what's wrong with your script then...  ;)  I just know where to download and what I want to download for my gdesklets.

---

