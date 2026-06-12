---
title: "Songbird Launcher help"
date: 2010-10-17
forum: General Help
---

### Post by Aaric on 2010-10-17
Ok, I got Songbird here: [http://techie-buzz.com/foss/download-songbird-1-8-0-for-linux.html]("http://techie-buzz.com/foss/download-songbird-1-8-0-for-linux.html")

I've been trying to make a launcher for it and everything i've tried doesn't work. I've tried browsing for it and i've fiddled around with a few commands, but I can't get anything to work.

Any ideas?

---

### Post by alexan on 2010-10-17
Songbird is no longer supported for linux: bad idea switch to it.

[http://www.getsongbird.com/system-requirements.php](http://www.getsongbird.com/system-requirements.php)

I do suggest you to find something more worthy. :guitar:

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
That's true! And soon will have Nightingale which is based on Songbird. Until then you can use Banshee. It's very good. Or Rhythmbox. On Lucid I had Songbird installed and working from this link: [http://www.ubuntuhq.com/content/download-songbird-180-linux](http://www.ubuntuhq.com/content/download-songbird-180-linux)
but it doesn't seem to work for me in Maverick. Where do you want to put the launcher?

---

### Post by Aaric on 2010-10-17
I know that it is no longer officially supported. There are community releases though. And I really, honestly don't like any of the other media players for Linux. Plus I have to use Zune because I have a Zune HD. So, I still want to make a launcher for Songbird.

---

### Post by Aaric on 2010-10-17
> **&#24746 said:**
> That's true! And soon will have Nightingale which is based on Songbird. Until then you can use Banshee. It's very good. Or Rhythmbox. On Lucid I had Songbird installed and working from this link: [http://www.ubuntuhq.com/content/download-songbird-180-linux](http://www.ubuntuhq.com/content/download-songbird-180-linux)
but it doesn't seem to work for me in Maverick. Where do you want to put the launcher?

On the Desktop, Panel, and in the main menu. Which if I can make one I can make them all.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
OK! Wait for me to download it and then I'll tell you!

---

### Post by Aaric on 2010-10-17
Ok. The article you linked to is the same download as where I got mine from(But mine has instructions), and it does work on 10.10.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
If you downloaded it from the link I gave you do these steps:

1) Go to System > Preferences > Main Menu
2) Select Sound & Video (on the left) and then new Item(on the right)
3) In name type Songbird (or anything you want really)
4) In command hit browse and then locate your extracted Songbird directory and select the file "songbird" (not songbird-bin or anything else) and then open
5) In comment write whatever you want to say when you hover your mouse over it (like Songbird media player or sth like that)
6) Press the launcher icon locate your Songbird directory again and select the .png with the bird
7) hit ok

Tell me if this works and then I'll tell you about the Desktop and panel
Edit: If the download is the same as mine then it will work for you. Maybe it's smth with my PC. I'll try it again

---

### Post by Aaric on 2010-10-17
Hmmm, for some reason I can't get it to run again at all....

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Why? What happens exactly? Go to terminal, cd to the Songbird directory and enter ./songbird. Tell me what it says...

---

### Post by Aaric on 2010-10-17
This is what I get.
> aaric@aaric-laptop:~/Songbird$ ./songbird

(songbird-bin:2165): GLib-GObject-WARNING **: cannot register existing type `GstVideoBalance'

(songbird-bin:2165): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(songbird-bin:2165): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(songbird-bin:2165): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(songbird-bin:2165): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(songbird-bin:2165): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstsubparse.so': /usr/lib/gstreamer-0.10/libgstsubparse.so: undefined symbol: gst_util_double_to_fraction

(songbird-bin:2165): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgnl.so': /usr/lib/gstreamer-0.10/libgnl.so: undefined symbol: gst_pad_link_full

(songbird-bin:2165): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdeinterlace.so': /usr/lib/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_event_parse_still_frame

(songbird-bin:2165): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsth264parse.so': /usr/lib/gstreamer-0.10/libgsth264parse.so: undefined symbol: gst_byte_writer_init_with_size

(songbird-bin:2165): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsttaglib.so': /usr/lib/gstreamer-0.10/libgsttaglib.so: undefined symbol: gst_tag_list_peek_string_index

(songbird-bin:2165): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstaiff.so': /usr/lib/gstreamer-0.10/libgstaiff.so: undefined symbol: gst_byte_writer_put_uint32_be

(songbird-bin:2165): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpegdemux.so': /usr/lib/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: gst_tag_get_language_code_iso_639_1

(songbird-bin:2165): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libfsfunnel.so': /usr/lib/gstreamer-0.10/libfsfunnel.so: undefined symbol: gst_pad_peer_get_caps_reffed

(songbird-bin:2165): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libresindvd.so': /usr/lib/gstreamer-0.10/libresindvd.so: undefined symbol: gst_video_event_parse_still_frame

(songbird-bin:2165): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdvdspu.so': /usr/lib/gstreamer-0.10/libgstdvdspu.so: undefined symbol: gst_video_event_parse_still_frame

(songbird-bin:2165): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': /usr/lib/gstreamer-0.10/libgstffmpeg.so: undefined symbol: gst_caps_set_value

(songbird-bin:2165): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstjpegformat.so': /usr/lib/gstreamer-0.10/libgstjpegformat.so: undefined symbol: gst_byte_writer_put_uint8

(songbird-bin:2165): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libfsrtpconference.so': /usr/lib/gstreamer-0.10/libfsrtpconference.so: undefined symbol: gst_pad_get_caps_reffed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_xml_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal


---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
That's what it says to me too. Has it worked for you before? I mean on Maverick.

---

### Post by Aaric on 2010-10-17
Yeah, when I first tried it...that was 3 days ago. I got it open and it was scanning for the library. I'm trying to see if I installed or removed something since then that might have messed with it.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
It seems like a function or variable it calls that doesn't exist or smth like that. I'm searching for a solution. We may  need to link the plugins with smth but I don't know with what exactly.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
OK! It worked for me. go to ~/Songbird/lib and delete the libgstreamer-0.10.so plugin. tell me how it goes

---

### Post by Aaric on 2010-10-17
I deleted it, but I get a different error... :( here it is:

> (gst-plugin-scanner:3394): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstqtdemux.so': /home/aaric/Songbird/gst-plugins/libgstqtdemux.so: undefined symbol: gst_tag_id3v2_read

(gst-plugin-scanner:3394): GLib-GObject-WARNING **: specified instance size for type `GstRTPDVPay' is smaller than the parent type's `GstBaseRTPPayload' instance size

(gst-plugin-scanner:3394): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gst-plugin-scanner:3394): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(gst-plugin-scanner:3394): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstid3demux.so': /home/aaric/Songbird/gst-plugins/libgstid3demux.so: undefined symbol: gst_tag_id3v2_read

(gst-plugin-scanner:3394): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstjpeg.so': libjpeg.so.7: cannot open shared object file: No such file or directory

(gst-plugin-scanner:3394): GLib-GObject-WARNING **: cannot register existing type `GstRTPDepay'

(gst-plugin-scanner:3394): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gst-plugin-scanner:3394): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(songbird-bin:3389): Gdk-WARNING **: gdk_window_set_icon_list: icons too large


And I also get this if I try to open it more than once, a good sign that at least it's trying to run.

"Songbird is already running, but is not responding. To open a new window, you must first close the existing Songbird process, or restart your system."

---

### Post by Aaric on 2010-10-17
Ok, I got it to run. But I had to run it like this: sudo -H ./songbird
I still get the same errors, but it runs. Could I make that into a launcher?

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Go to System > Administration > System Monitor and choose the "Processes" tab. Then find songbird and songbird-bin and end them. Finally, try and run songbird again. I hope it works. I'll be waiting for your reply...

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Do what I said and if it doesn't work I'll try and make it work with they way you got it running.

---

### Post by Aaric on 2010-10-17
Nope, they aren't even there. Well, unless I run it with the command I used above...
I have the Sys Monitor set to view all processes and when I just double click, or right-click 'Open' on 'songbird' nothing shows up in the Sys Monitor

Edit: I also tried just 'gksudo ./songbird' and that works too...

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
What's not where? You mean the processes? That would just help you with the warning that songbird's already running. When you close Songbird and run it again does it run?  I mean if you either click on the songbird file inside ~/Songbird or run ./songbird in terminal. Do that, not the command you told me and if it doesn't work I'll tell you what to do. If you run it in terminal and runs fine but gives you warnings don't mind them much.

---

### Post by Aaric on 2010-10-17
I know, that's my point. For some reason it doesn't even show up as running when I click on it. It won't run without sudo. It won't work if I click on it, or just run ./songbird (and, yes, I am cd'd into the Songbird folder). Nothing happens without root privileges. I tried logging in as root and just double clicking on it and it runs fine, same with running ./songbird when i'm logged in as root.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Go to terminal, cd in the folder ~/Songbird and type ls - l. The songbird file should have x permissions. Type "sudo chmod +x songbird" anyway (without the quotes) and try again. I'm almost 99% sure that will work. Either way tell me about it.

---

### Post by Aaric on 2010-10-17
> **&#24746 said:**
> Go to terminal, cd in the folder ~/Songbird and type ls - l. The songbird file should have x permissions. Type "sudo chmod +x songbird" anyway (without the quotes) and try again. I'm almost 99% sure that will work. Either way tell me about it.

Ok, I want to make sure I have this right. I think i'm misunderstanding the first part. I need to use -I when I cd into the folder?

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
ls -l. But go ahead and skip that part. Type the second command I told you. The first is to view a long description of your files which also displays the permissions. But if you type "sudo chmod +x songbird" it will give it the permissions we want anyway. So just type that. Then if you have songbird running close it and run it again. And of course do all those as a regular user because we want it to run for you and not only for the root user.

---

### Post by Aaric on 2010-10-17
Ok, I do that. Nothing happens in the terminal. And I still can't run it... I ran the first comand you told me to and I get this line for 'songbird' after the 'sudo chmod +x songbird' command

> -rwxrwxrwx  1 aaric aaric  12173 2010-08-30 18:02 songbird

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
First are you logged in as a regular user? That doesn't have to do anything with the problem but I ask because of the reason I mentioned. The chmod command doesn't give an output in terminal. But with the results of the ls -l command you showed me it seems that you have execute permission for the file. So it should run. I don't understand what's the problem though. Did you run it on terminal? If you did, what was the output? Sorry, that I haven't helped you yet but it's a little difficult doing it via the internet. But I won't rest till I help you :)

---

### Post by Aaric on 2010-10-17
> **&#24746 said:**
> First are you logged in as a regular user? That doesn't have to do anything with the problem but I ask because of the reason I mentioned. The chmod command doesn't give an output in terminal. But with the results of the ls -l command you showed me it seems that you have execute permission for the file. So it should run. I don't understand what's the problem though. Did you run it on terminal? If you did, what was the output? Sorry, that I haven't helped you yet but it's a little difficult doing it via the internet. But I won't rest till I help you :)

Ok, thanks...I have to walk away from the  comp for a few min, but  to answer your questions: yes I am logged in as a regular user, and I get the same errors I git from the last post when I mentioned them. I get the same when running it as root, but a few of the messages are duplicated and it actually runs.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
OK! When you come back I'll still be here and I'll help you. I want you to tell me what's the output when you run it on terminal though. If it worked for me I'm sure it will work for you too. Again, sorry about not having helped you yet!

---

### Post by Aaric on 2010-10-17
Ok, sorry about that. I'm back, thanks for the help, I appreciate it.
Heres what I get while just running './songbird':

> aaric@aaric-laptop:~/Songbird$  ./songbird

(gst-plugin-scanner:5253): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstqtdemux.so': /home/aaric/Songbird/gst-plugins/libgstqtdemux.so: undefined symbol: gst_tag_id3v2_read

(gst-plugin-scanner:5253): GLib-GObject-WARNING **: specified instance size for type `GstRTPDVPay' is smaller than the parent type's `GstBaseRTPPayload' instance size

(gst-plugin-scanner:5253): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gst-plugin-scanner:5253): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(gst-plugin-scanner:5253): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstid3demux.so': /home/aaric/Songbird/gst-plugins/libgstid3demux.so: undefined symbol: gst_tag_id3v2_read

(gst-plugin-scanner:5253): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstjpeg.so': libjpeg.so.7: cannot open shared object file: No such file or directory

(gst-plugin-scanner:5253): GLib-GObject-WARNING **: cannot register existing type `GstRTPDepay'

(gst-plugin-scanner:5253): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gst-plugin-scanner:5253): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(songbird-bin:5248): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

And here's what I get when I use 'sudo -H' or 'gksudo':

> aaric@aaric-laptop:~/Songbird$ sudo -H ./songbird
[sudo] password for aaric: 

(gst-plugin-scanner:5516): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstqtdemux.so': /home/aaric/Songbird/gst-plugins/libgstqtdemux.so: undefined symbol: gst_tag_id3v2_read

(gst-plugin-scanner:5516): GLib-GObject-WARNING **: specified instance size for type `GstRTPDVPay' is smaller than the parent type's `GstBaseRTPPayload' instance size

(gst-plugin-scanner:5516): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gst-plugin-scanner:5516): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(gst-plugin-scanner:5516): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstid3demux.so': /home/aaric/Songbird/gst-plugins/libgstid3demux.so: undefined symbol: gst_tag_id3v2_read

(gst-plugin-scanner:5516): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstjpeg.so': libjpeg.so.7: cannot open shared object file: No such file or directory

(gst-plugin-scanner:5516): GLib-GObject-WARNING **: cannot register existing type `GstRTPDepay'

(gst-plugin-scanner:5516): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gst-plugin-scanner:5516): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(songbird-bin:5510): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:5510): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:5510): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

I haven't compared them side by side, but the only thing that seems different is the number after 'songbird-bin:****'(which I doubt even matters) and the fact that it repeats the last error.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
OK! If you aren't bored yet delete the directory Songbird and the launcher you created and download it again from the link you gave me. Follow the instructions on that website except for the final one which is "./songbird". Then go to ~/Songbird/lib and delete gstreamer-0.10.so. Finally run it on terminal (./songbird) and if it runs create the launcher again and tell me the results. Another problem came up and I want to see if you ' ll have it when songbird finally runs for you.

---

### Post by Aaric on 2010-10-17
It still won't run.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Actually, after you do all those steps and before you delete the gstreamer-0.10.so launch the terminal and type "cd ~/Songbird/lib && rm -r libgst*.so". Then type "cd .. && ./songbird". That fixes the other problem I told you about.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Do as I said in the last post even if you already have deleted the gstreamer-0.10.so

---

### Post by Aaric on 2010-10-17
Still nothing, but I did make a Launcher with 'gksudo ./Songbird/songbird' and that works...

---

### Post by Aaric on 2010-10-17
I don't know if this is relevant or not, but I wipe my HDD and re-install Windows and Ubuntu every so often and I installed Ubuntu with the 10.10 beta CD, but I did install all the updates so it should be like a regular release.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Well not quite. Beta releases tend to be buggy. I can't see a reason why one shouldn't install the alpha version but if you want it that way for a reason I guess it's fine. That could be the reason why it doesn't run though. You see, I think that songbird tries to use its plugins and they aren't compatible with Meerkat or any version really. That's why you had to delete all of them, so that it used the ones located in /usr/lib/gstreamer-0.10. Of course, there's always the possibility I'm wrong. As long as you continue to have the beta release and songbird doesn't run I can't know for sure. When the alpha wasn't out yet, I had installed the beta version inside VBox and even Rhythmbox used to crash. If you can post some screenshots of the results when you try to run it.

---

### Post by Aaric on 2010-10-17
Well, from what I read here: [http://ubuntuforums.org/showthread.php?t=1500648]("http://ubuntuforums.org/showthread.php?t=1500648") it says that it upgrades automatically from the Beta/Alpha. Yeah, give me a min and i'll put up a screenshot.

---

### Post by Aaric on 2010-10-17
When I run it in the terminal I get this:

[IMG]http://www.mediafire.com/imgbnc.php/712d54cd2aca755421b810124ad6e0ff6g.jpg[/IMG]

And when I double click, or right click 'Open' I get this window and bothing happens after I click Run, or Run in Termianl:

[IMG]http://www.mediafire.com/imgbnc.php/ea6e47a1322a4eef0923bbda9ae495d56g.jpg[/IMG]

Sorry about the delay .

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Well, try this for one last time;launch the terminal and type these:

1) cd ~/Songbird/lib
2) rm -r libgst*.so
3) cd ..
4) ./songbird

I hope the output isn't the same. However, I couldn't help but notice that it says that it can't find the plugin inside gst-plugins. Is there a possibility that when I told you to delete all the libgst*.so plugins you deleted them from the wrong directory? I don't remember getting that message and I downloaded it from the same link. if that doesn't work I'll try to post my files.

---

### Post by Aaric on 2010-10-17
Ok, I started from the beginning.

[IMG]http://www.mediafire.com/imgbnc.php/3ffc49172e45f945687f36c0f3eb77376g.jpg[/IMG]

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
If that doesn't run take this compressed plugin uncompress it and put the .so file inside ~/Songbird/gst-plugins. You might have to change the ownership of it so that it belongs to you, but more on that if it doesn't work like that. Hopefully, I attached the file successfully!

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Oh, I forgot these. Do the same with them. I hope I didn't forget anything else.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
I just noticed the time on your screenshot. Here it's Monday 18th, 06:20 AM. I'm in the future! :)

---

### Post by Aaric on 2010-10-17
Haha, you're in Greece? I'm in Florida...
I tried extracting those and I had to replace the ones that were already in the folder, and then I checked to make sure I had the right permissions. And I tried to run it again same thing, same error.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Do this:

1) launch a terminal
2) cd ~/Songbird/gst-plugins
3) sudo chown aaric libgst*.so

If that doesn't work either replace your Songbird directory with the one I'm posting. I don't know if you'll be the owner of it after that so if it doesn't work you'll probably have to change the ownership of everything in it including the directory itself. If it comes to his and you need help with that ask me. But I'm waiting in case the above steps work. 

Edit: Sorry for the delay. It seems I can't post my directory here 'cause it exceeds the forum's limit. Try this link instead
[http://rapidshare.com/files/425712663/Songbird.tar.gz](http://rapidshare.com/files/425712663/Songbird.tar.gz)
 Sadly, this link won't be available to other people who might have the same problem in the future.

---

### Post by Aaric on 2010-10-18
Ok, I cd'd to the 'Songbird' folder(the one you had me download) after I replaced mine. And I did this 'sudo chown aaric *.*' and I ran 'ls -l' and it looks like it worked. But I still can't get it to run without root privelages.

---

### Post by Aaric on 2010-10-18
Oh, and i'll upload the Songbird folder to Mediafire and put it up here.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-18
OK, just in case type:
1)  sudo chown aaric Songbird
2)  cd Songbird
3)  sudo chown aaric */*/*/* 

That changes the ownership of files up to the fourth level of hierarchy. In other words if you have a file inside /folder/subfolder1/subfolder2/file then you change it's ownership with that command. With what you typed you only changed it for all the files on the first level. I'll try and find some other way in case this doesn't work.

---

### Post by Aaric on 2010-10-18
Ah, I see. That makes sense. Ok, I ran that and this is what I get:

> aaric@aaric-laptop:~/Songbird$ ./songbird

(gst-plugin-scanner:9364): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstqtdemux.so': /home/aaric/Songbird/gst-plugins/libgstqtdemux.so: undefined symbol: gst_tag_id3v2_read

(gst-plugin-scanner:9364): GLib-GObject-WARNING **: specified instance size for type `GstRTPDVPay' is smaller than the parent type's `GstBaseRTPPayload' instance size

(gst-plugin-scanner:9364): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gst-plugin-scanner:9364): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(gst-plugin-scanner:9364): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstid3demux.so': /home/aaric/Songbird/gst-plugins/libgstid3demux.so: undefined symbol: gst_tag_id3v2_read

(gst-plugin-scanner:9364): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstmozilla.so': libxpcom.so: cannot open shared object file: No such file or directory

(gst-plugin-scanner:9364): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstjpeg.so': libjpeg.so.7: cannot open shared object file: No such file or directory

(gst-plugin-scanner:9364): GLib-GObject-WARNING **: cannot register existing type `GstVideoBalance'

(gst-plugin-scanner:9364): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(gst-plugin-scanner:9364): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(gst-plugin-scanner:9364): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gst-plugin-scanner:9364): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(gst-plugin-scanner:9364): GLib-GObject-WARNING **: cannot register existing type `GstRTPDepay'

(gst-plugin-scanner:9364): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gst-plugin-scanner:9364): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)

(songbird-bin:9359): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(gst-plugin-scanner:9376): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstqtdemux.so': /home/aaric/Songbird/gst-plugins/libgstqtdemux.so: undefined symbol: gst_tag_id3v2_read

(gst-plugin-scanner:9376): GLib-GObject-WARNING **: specified instance size for type `GstRTPDVPay' is smaller than the parent type's `GstBaseRTPPayload' instance size

(gst-plugin-scanner:9376): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gst-plugin-scanner:9376): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(gst-plugin-scanner:9376): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstid3demux.so': /home/aaric/Songbird/gst-plugins/libgstid3demux.so: undefined symbol: gst_tag_id3v2_read

(gst-plugin-scanner:9376): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstmozilla.so': libxpcom.so: cannot open shared object file: No such file or directory

(gst-plugin-scanner:9376): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstjpeg.so': libjpeg.so.7: cannot open shared object file: No such file or directory

(gst-plugin-scanner:9376): GStreamer-WARNING **: Failed to load plugin '/home/aaric/Songbird/gst-plugins/libgstqtdemux.so': /home/aaric/Songbird/gst-plugins/libgstqtdemux.so: undefined symbol: gst_tag_id3v2_read

And it just leaves it open, it doesn't go back to 'aaric@aaric-laptop:~/Songbird/$'

And it's also showing up in the Sys Monitor as running, but nothing is showing

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-18
To correct that just press Ctrl+C. It will end the running process. The only explanation I can think of is that there's a problem with the plugins inside /usr/lib/gstreamer-0.10. If I had the same problem I would try reinstalling them but I won't suggest you do it because I might be wrong and I don't want to mess anyone's computer without being 100% sure about smth. I would really want to see the permissions of your files inside ~/Songbird. Can you post a screenshot of a ls -l inside that directory? Meanwhile I'll try to install the 10.10 beta in VBox and see if the problem exists there.

---

### Post by Aaric on 2010-10-18
> aaric@aaric-laptop:~/Songbird$ ls -l
total 288
-rw-r--r--  1 aaric aaric    346 2010-08-30 18:02 application.ini
-rw-r--r--  1 aaric aaric    113 2010-08-30 18:02 blocklist.xml
drwxr-xr-x  3 aaric aaric   4096 2010-10-17 23:59 chrome
drwxr-xr-x  2 aaric aaric  12288 2010-10-17 23:59 components
drwxr-xr-x  4 aaric aaric   4096 2010-10-17 23:59 defaults
drwxr-xr-x  5 aaric aaric   4096 2010-10-17 23:59 extensions
drwxr-xr-x  2 aaric aaric   4096 2010-10-17 23:59 gst-plugins
drwxr-xr-x  3 aaric aaric   4096 2010-10-17 23:59 gstreamer
drwxr-xr-x  2 aaric aaric   4096 2010-10-17 23:59 jsmodules
drwxr-xr-x  2 aaric aaric   4096 2010-10-17 23:59 lib
-rw-r--r--  1 aaric aaric  30828 2010-08-30 18:12 libjemalloc.so
-rw-r--r--  1 aaric aaric  30916 2010-08-30 18:12 LICENSE.html
drwxr-xr-x  2 aaric aaric   4096 2010-08-30 18:02 plugins
-rw-r--r--  1 aaric aaric   1125 2010-08-30 18:12 README.txt
drwxr-xr-x  2 aaric aaric   4096 2010-10-17 23:59 scripts
drwxr-xr-x  2 aaric aaric   4096 2010-10-17 23:59 searchplugins
-rwxr-xr-x  1 aaric aaric  12173 2010-08-30 18:02 songbird
-rw-r--r--  1 aaric aaric 100308 2010-08-30 18:12 songbird-512.png
-rwxr-xr-x  1 aaric aaric  27360 2010-05-02 20:57 songbird-bin
-rw-r--r--  1 aaric aaric    191 2010-08-30 18:02 songbird.ini
-rw-r--r--  1 aaric aaric    260 2010-08-30 18:12 TRADEMARK.txt
-rw-r--r--  1 aaric aaric    274 2010-08-30 18:02 updater.ini
drwxr-xr-x  3 aaric aaric   4096 2010-10-17 23:59 updates
drwxr-xr-x 12 aaric aaric   4096 2010-10-17 23:59 xulrunner

But, remember I have all the updates installed too. And when I first re-installed 10.10 I installed almost all the codecs in the repository. How would I reinstall them, i'm willing to try it.

Edit: Oh, and I recently installed 'XVidCap Screen Capture' and it had me remove some things things...i'll check on those....those were these:

[IMG]http://www.mediafire.com/imgbnc.php/2ce9ceacd59a6443593c501e55fc0fd26g.jpg[/IMG]

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-18
I'm sorry! I meant to say the gst-plugins directory. I also forgot to ask you smth extremely important. Are you running a 32-bit version or a 64-bit? Also if you had a mirror of Ubuntu 10.10 beta and could send it to me it would be helpful because I have deleted mine from my PC.

---

### Post by Aaric on 2010-10-18
32 bit. And nope, sorry I just have a CD copy, and horrible upload speeds. This is the original torrent, so you can try this. I don't know if anyone's seeding it though.
[http://isohunt.com/lite/files/209723501/Ubuntu]("http://isohunt.com/lite/files/209723501/Ubuntu")

Edit: Whoops I forgot this:

> aaric@aaric-laptop:~/Songbird/gst-plugins$ ls -l
total 6304
-rwxr-xr-x 1 aaric aaric   28828 2010-08-30 18:12 libgstadder.so
-rwxr-xr-x 1 aaric aaric   12872 2010-08-30 18:12 libgstadpcmdec.so
-rwxr-xr-x 1 aaric aaric   13580 2010-08-30 18:12 libgstadpcmenc.so
-rwxr-xr-x 1 aaric aaric   42232 2010-08-30 18:12 libgstaiffparse.so
-rwxr-xr-x 1 aaric aaric   18872 2010-08-30 18:12 libgstalaw.so
-rwxr-xr-x 1 aaric aaric   10312 2010-08-30 18:12 libgstalphacolor.so
-rwxr-xr-x 1 aaric aaric   19836 2010-08-30 18:12 libgstalpha.so
-rwxr-xr-x 1 aaric aaric   97888 2010-08-30 18:12 libgstalsa.so
-rwxr-xr-x 1 aaric aaric   13448 2010-08-30 18:12 libgstapetag.so
-rwxr-xr-x 1 aaric aaric   45540 2010-08-30 18:12 libgstasfmux.so
-rwxr-xr-x 1 aaric aaric  127464 2010-08-30 18:12 libgstasf.so
-rwxr-xr-x 1 aaric aaric   60580 2010-08-30 18:12 libgstaudioconvert.so
-rwxr-xr-x 1 aaric aaric  104052 2010-08-30 18:12 libgstaudiofx.so
-rwxr-xr-x 1 aaric aaric   19656 2010-08-30 18:12 libgstaudiorate.so
-rwxr-xr-x 1 aaric aaric   69612 2010-08-30 18:12 libgstaudioresample.so
-rwxr-xr-x 1 aaric aaric   33448 2010-08-30 18:12 libgstaudiotestsrc.so
-rwxr-xr-x 1 aaric aaric   19340 2010-08-30 18:12 libgstauparse.so
-rwxr-xr-x 1 aaric aaric   36860 2010-08-30 18:12 libgstautodetect.so
-rwxr-xr-x 1 aaric aaric  163468 2010-08-30 18:12 libgstavi.so
-rwxr-xr-x 1 aaric aaric  202504 2010-08-30 18:12 libgstcoreelements.so
-rwxr-xr-x 1 aaric aaric    8408 2010-08-30 18:12 libgstcoreindexers.so
-rwxr-xr-x 1 aaric aaric   16936 2010-08-30 18:12 libgstcutter.so
-rwxr-xr-x 1 aaric aaric  101940 2010-08-30 18:12 libgstdecodebin2.so
-rwxr-xr-x 1 aaric aaric   45144 2010-08-30 18:12 libgstdecodebin.so
-rwxr-xr-x 1 aaric aaric   67628 2010-08-30 18:12 libgsteffectv.so
-rwxr-xr-x 1 aaric aaric   24884 2010-08-30 18:12 libgstequalizer.so
-rwxr-xr-x 1 aaric aaric  239636 2010-08-30 18:12 libgstffmpegcolorspace.so
-rwxr-xr-x 1 aaric aaric   90684 2010-08-30 18:12 libgstflac.so
-rwxr-xr-x 1 aaric aaric 1400132 2010-08-30 18:12 libgstflump3dec.so
-rwxr-xr-x 1 aaric aaric   35520 2010-08-30 18:12 libgstgdp.so
-rwxr-xr-x 1 aaric aaric  107968 2010-08-30 18:12 libgstgoom.so
-rwxr-xr-x 1 aaric aaric   14600 2010-08-30 18:12 libgsticydemux.so
-rwxr-xr-x 1 aaric aaric    9064 2010-08-30 18:12 libgstid3demux.so
-rwxr-xr-x 1 aaric aaric   39980 2010-08-30 18:12 libgstid3tag.so
-rwxr-xr-x 1 aaric aaric   65064 2010-08-30 18:12 libgstjpeg.so
-rwxr-xr-x 1 aaric aaric   21096 2010-08-30 18:12 libgstlevel.so
-rwxr-xr-x 1 aaric aaric  196628 2010-08-30 18:12 libgstmatroska.so
-rwxr-xr-x 1 aaric aaric   82160 2010-08-30 18:12 libgstmozilla.so
-rwxr-xr-x 1 aaric aaric   22908 2010-08-30 18:12 libgstmpeg4videoparse.so
-rwxr-xr-x 1 aaric aaric   70652 2010-08-30 18:12 libgstmpegaudioparse.so
-rwxr-xr-x 1 aaric aaric   13492 2010-08-30 18:12 libgstmulaw.so
-rwxr-xr-x 1 aaric aaric   14852 2010-08-30 18:12 libgstmultifile.so
-rwxr-xr-x 1 aaric aaric   27488 2010-08-30 18:12 libgstmultipart.so
-rwxr-xr-x 1 aaric aaric  144984 2010-08-30 18:12 libgstogg.so
-rwxr-xr-x 1 aaric aaric  226588 2010-08-30 18:12 libgstplaybin.so
-rwxr-xr-x 1 aaric aaric   87652 2010-08-30 18:12 libgstpulse.so
-rwxr-xr-x 1 aaric aaric  188476 2010-08-30 18:12 libgstqtdemux.so
-rwxr-xr-x 1 aaric aaric   98328 2010-08-30 18:12 libgstqtmux.so
-rwxr-xr-x 1 aaric aaric   58424 2010-08-30 18:12 libgstqueue2.so
-rwxr-xr-x 1 aaric aaric   41348 2010-08-30 18:12 libgstreplaygain.so
-rwxr-xr-x 1 aaric aaric  214244 2010-08-30 18:12 libgstrtpmanager.so
-rwxr-xr-x 1 aaric aaric  314520 2010-08-30 18:12 libgstrtp.so
-rwxr-xr-x 1 aaric aaric  118636 2010-08-30 18:12 libgstrtsp.so
-rwxr-xr-x 1 aaric aaric   28864 2010-08-30 18:12 libgstsdpelem.so
-rwxr-xr-x 1 aaric aaric   42220 2010-08-30 18:12 libgstselector.so
-rwxr-xr-x 1 aaric aaric   57184 2010-08-30 18:12 libgstsmpte.so
-rwxr-xr-x 1 aaric aaric   17260 2010-08-30 18:12 libgstspectrum.so
-rwxr-xr-x 1 aaric aaric   73928 2010-08-30 18:12 libgsttheora.so
-rwxr-xr-x 1 aaric aaric   70444 2010-08-30 18:12 libgsttypefindfunctions.so
-rwxr-xr-x 1 aaric aaric   53492 2010-08-30 18:12 libgstudp.so
-rwxr-xr-x 1 aaric aaric   14536 2010-08-30 18:12 libgstvideobalance.so
-rwxr-xr-x 1 aaric aaric   22728 2010-08-30 18:12 libgstvideobox.so
-rwxr-xr-x 1 aaric aaric   33600 2010-08-30 18:12 libgstvideocrop.so
-rwxr-xr-x 1 aaric aaric   17672 2010-08-30 18:12 libgstvideoflip.so
-rwxr-xr-x 1 aaric aaric   56736 2010-08-30 18:12 libgstvideomixer.so
-rwxr-xr-x 1 aaric aaric   28476 2010-08-30 18:12 libgstvideorate.so
-rwxr-xr-x 1 aaric aaric   81364 2010-08-30 18:12 libgstvideoscale.so
-rwxr-xr-x 1 aaric aaric   45072 2010-08-30 18:12 libgstvideotestsrc.so
-rwxr-xr-x 1 aaric aaric   17372 2010-08-30 18:12 libgstvolume.so
-rwxr-xr-x 1 aaric aaric   78024 2010-08-30 18:12 libgstvorbis.so
-rwxr-xr-x 1 aaric aaric   13724 2010-08-30 18:12 libgstwavenc.so
-rwxr-xr-x 1 aaric aaric   56004 2010-08-30 18:12 libgstwavparse.so
-rwxr-xr-x 1 aaric aaric   49784 2010-08-30 18:12 libgstximagesink.so
-rwxr-xr-x 1 aaric aaric   72584 2010-08-30 18:12 libgstxvimagesink.so


---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-18
You can try this on terminal:

> sudo apt-get install gstreamer*

Of course some of those may not be needed. But it's hard for me to look  for the specific ones that are. Try this and tell me how it goes.

PS: If it's 32-bit it's better because there's usually better support especially on codecs.

---

### Post by Aaric on 2010-10-18
When I do that, this is what I get:

```
aaric@aaric-laptop:~$ sudo apt-get install gstreamer*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'bluez-gstreamer' for regex 'gstreamer*'
Note, selecting 'libgstreamer-plugins-base0.10-0' for regex 'gstreamer*'
Note, selecting 'libgstreamer0.10-0' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-base' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-good' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-x' for regex 'gstreamer*'
Note, selecting 'gir1.0-gstreamer-0.10' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-alsa' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-audiosink' for regex 'gstreamer*'
Note, selecting 'gstreamer-tools' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-tools' for regex 'gstreamer*'
Note, selecting 'gstreamer0.8-tools' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-audiosource' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-doc' for regex 'gstreamer*'
Note, selecting 'libgstreamer0.10-dev' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-esd' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-gnonlin' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-gnonlin-dbg' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-gnonlin-doc' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-nice' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-bad' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-videosource' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-base-apps' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-base-dbg' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-gnomevfs' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-bad-dbg' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-base-doc' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-really-bad' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-good-doc' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-videosink' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-visualization' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-good-dbg' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-pulseaudio' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-fluendo-mp3' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-ugly' for regex 'gstreamer*'
Note, selecting 'libcanberra-gstreamer' for regex 'gstreamer*'
Note, selecting 'libcanberra-gstreamer-dbg' for regex 'gstreamer*'
Note, selecting 'gstreamer-codec-install' for regex 'gstreamer*'
Note, selecting 'totem-gstreamer' for regex 'gstreamer*'
Note, selecting 'libgstreamer-plugins-base0.10-dev' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins' for regex 'gstreamer*'
Note, selecting 'libgstreamer0.10-0-dbg' for regex 'gstreamer*'
Note, selecting 'phonon-backend-gstreamer' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-ffmpeg' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-ugly-dbg' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-bad-multiverse' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-ugly-multiverse' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-buzztard' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-cutter' for regex 'gstreamer*'
Note, selecting 'deejayd-gstreamer' for regex 'gstreamer*'
Note, selecting 'libgstreamer-perl' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-ugly-doc' for regex 'gstreamer*'
Note, selecting 'gstreamer-dbus-media-service' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-buzztard-doc' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-ffmpeg-dbg' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-packagekit' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-pitfdll' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-fluendo-mpegdemux' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-fluendo-mpegmux' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-farsight' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-schroedinger' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-sdl' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-bad-doc' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-pocketsphinx' for regex 'gstreamer*'
Note, selecting 'libghc6-gstreamer-dev' for regex 'gstreamer*'
Note, selecting 'libghc6-gstreamer-doc' for regex 'gstreamer*'
Note, selecting 'libghc6-gstreamer-prof' for regex 'gstreamer*'
Note, selecting 'libghc6-gstreamer-dev-0.11.0-375eb' for regex 'gstreamer*'
Note, selecting 'libghc6-gstreamer-prof-0.11.0-375eb' for regex 'gstreamer*'
Note, selecting 'libgstreamer-interfaces-perl' for regex 'gstreamer*'
Note, selecting 'libgstreamermm-0.10-2' for regex 'gstreamer*'
Note, selecting 'libgstreamermm-0.10-dbg' for regex 'gstreamer*'
Note, selecting 'libgstreamermm-0.10-dev' for regex 'gstreamer*'
Note, selecting 'libgstreamermm-0.10-doc' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-lame' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-ffmpeg-full' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-bad-multiverse-dbg' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-ugly-multiverse-dbg' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-fluendo-plugins-mp3-partner' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-fluendo-plugins' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-fluendo-plugins-mp3' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-fluendo-plugins-offline' for regex 'gstreamer*'
Note, selecting 'gstreamer0.10-plugins-good' instead of 'gstreamer0.10-visualization'
Note, selecting 'gstreamer0.10-plugins-bad' instead of 'gstreamer0.10-fluendo-mpegdemux'
Note, selecting 'gstreamer0.10-plugins-bad' instead of 'gstreamer0.10-fluendo-mpegmux'
Note, selecting 'gstreamer0.10-plugins-bad' instead of 'gstreamer0.10-plugins-farsight'
Note, selecting 'gstreamer0.10-plugins-bad' instead of 'gstreamer0.10-schroedinger'
Note, selecting 'libghc6-gstreamer-dev' instead of 'libghc6-gstreamer-dev-0.11.0-375eb'
Note, selecting 'libghc6-gstreamer-prof' instead of 'libghc6-gstreamer-prof-0.11.0-375eb'
Note, selecting 'gstreamer0.10-plugins-ugly-multiverse' instead of 'gstreamer0.10-lame'
Note, selecting 'gstreamer0.10-fluendo-plugins-mp3-partner' instead of 'gstreamer0.10-fluendo-plugins-mp3'
bluez-gstreamer is already the newest version.
gstreamer0.10-alsa is already the newest version.
gstreamer0.10-gnonlin is already the newest version.
gstreamer0.10-nice is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-base-apps is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-pulseaudio is already the newest version.
gstreamer0.10-tools is already the newest version.
gstreamer0.10-x is already the newest version.
libgstreamer-plugins-base0.10-0 is already the newest version.
libgstreamer0.10-0 is already the newest version.
libgstreamer0.10-0-dbg is already the newest version.
libgstreamer0.10-dev is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-ffmpeg set to manually installed.
gstreamer0.10-fluendo-mp3 is already the newest version.
gstreamer0.10-pitfdll is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad set to manually installed.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly set to manually installed.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-bad-multiverse set to manually installed.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
gstreamer0.10-plugins-ugly-multiverse set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gstreamer0.10-fluendo-plugins-mp3-partner : Conflicts: gstreamer0.10-fluendo-mp3
E: Broken packages

```

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-18
That's what caught my eye

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The reason I quoted that is because it's warning you about the "unstable" version. So it may be that you are using a beta version that's not fully supported.
Anyway, what happened with songbird? Did it run or did it fail as usual with the same output in terminal? If it did fail then I'm afraid there's not much I can do right now. Tomorrow (well for me today :) ) I'll try to find some workaround.

---

### Post by Aaric on 2010-10-18
Nope, didn't run. I set up the Launcher with the 'gksudo ./Songbird/songbird' and that works. So if you can't find a workaround I can just do that. Thanks for the help by the way.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-18
Don't mention it! I'll try and find something anyway.

PS: I noticed that the thread was about creating a launcher and we got slightly out of topic. I hope it's fine. Check again tomorrow in case I find something.

---

### Post by Aaric on 2010-10-18
Yeah, true. But before it was working. I just wasn't able to figure out the launcher part.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-18
But I can't understand why. Creating a launcher isn't supposed to create any problem at all. You said that it worked three days ago so maybe the things you installed or uninstalled on the last three days have something to do with this problem. Think back and try to undo some changes to see if it has any effect on the current situation. Hopefully I'll find something too.

---

### Post by Aaric on 2010-10-18
I don't know if you noticed it or not cause I was editing it an dyou posted, but I some things were removed when I installed a Screen capture program, and some the next day too(14th and 15th), and the 14th was when I originally tried it. Here's the post: [http://ubuntuforums.org/showpost.php?p=9989494&postcount=52]("http://ubuntuforums.org/showpost.php?p=9989494&postcount=52")

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-18
Well, you can install them again via synaptic or terminal. They may be dependencies. Once you try it let me know.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-20
Well, what happened with songbird? Did you make it work? Have you installed the packages you had removed yet? I have to warn you though, even if you make it work it has some bugs. If you by any chance managed to make it work and it says that it's running but with no response enter this on terminal
> killall songbird-bin
You might also need that if your system can't shut down because songbird is still running. I'm not sure if you'll see this but if you do tell me what happened...

PS: The "killall" command ends a process using its name. Alternatively you can end it with the "kill" command if you know its ID. Enter "man ps" in terminal for more information about processes.

---

### Post by The Bushman on 2010-10-26
Had the same problem then I saw this video on you tube. [http://www.youtube.com/watch?v=1t2Q_MXSzDY](http://www.youtube.com/watch?v=1t2Q_MXSzDY) solved the problem.
Also before I did the above I un-installed songbird completely using synaptics. Restarted. Then did what the video suggests. Worked like magic. Am using maverick:guitar:

---

