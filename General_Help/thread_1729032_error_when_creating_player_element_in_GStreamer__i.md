---
title: "error when creating player element in GStreamer  in Ubuntu"
date: 2011-04-14
forum: General Help
---

### Post by ap2011 on 2011-04-14
Hello All, 

I am facing error when I am creating player.

when am creating  the player element as follows 
     player = gst_element_factory_make("oggvorbisplayer", "player");
     
     g_object_set(player, "location" , argv[1] ,NULL);

     gst_element_set_state(GST_ELEMENT(player), GST_STATE_PLAYING);

I am getting these errors:

$./prac2 Hello.ogg  

(prac2:1870): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed 

(prac2:1870): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed 
  

I have installed in my Ubuntu machine (Ubuntu 10.04.2 LTS) the following GStreamer plugins : 
gstreamer0.10-tools 0.10.28.1  
gstreamer0.10-alsa  0.10.28.1 
gstreame0.10-ffmpeg  0.10.10.1 
gstreamer-plugin-base          0.10.28.1 
gstreamer-plugin-good        0.10.21 
gstreamer-plugin-ugly         0.10.14.1 
gstreamer-plugin-ugly-m         0.10.14  
gstreamer-plugin-bad           0.10.18           
totem                                2.30.2  

Please correct me what I am doing wrong.
Thanks in advance.

---

