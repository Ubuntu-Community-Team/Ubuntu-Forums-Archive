---
title: "gstreamer typefind problem"
date: 2012-03-08
forum: General Help
---

### Post by Ubuntee1 on 2012-03-08
```

#include <gst/gst.h>
#include <glib.h>
static GMainLoop *loop;
static gboolean my_bus_callback (GstBus *bus,GstMessage *message,gpointer data)
{
g_print ("Got %s message\n", GST_MESSAGE_TYPE_NAME (message));
switch (GST_MESSAGE_TYPE (message)) {
case GST_MESSAGE_ERROR: {
GError *err;
gchar *debug;
gst_message_parse_error (message, &err, &debug);
g_print ("Error: %s\n", err->message);
g_error_free (err);
g_free (debug);
g_main_loop_quit (loop);
break;
}
case GST_MESSAGE_EOS:
/* end-of-stream */
g_main_loop_quit (loop);
break;
default:
/* unhandled message */
break;
}
/* we want to be notified again the next time there is a message
* on the bus, so returning TRUE (FALSE means we want to stop watching
* for messages on the bus and our callback should not be called again)
*/
return TRUE;
}
static gboolean idle_exit_loop (gpointer data)
{
g_main_loop_quit ((GMainLoop *) data);
/* once */
return FALSE;
}
static void cb_typefound (GstElement *typefind,guint probability,GstCaps *caps,gpointer data)
{
GMainLoop *loop = data;
gchar *type;
type = gst_caps_to_string (caps);
g_print ("Media type %s found, probability %d%%\n", type, probability);
g_free (type);
/* since we connect to a signal in the pipeline thread context, we need
* to set an idle handler to exit the main loop in the mainloop context.
* Normally, your app should not need to worry about such things. */
g_idle_add (idle_exit_loop, loop);
}
gint main (gint argc,gchar *argv[])
{
GMainLoop *loop;
GstElement *pipeline, *filesrc, *typefind, *fakesink;
GstBus *bus;
/* init GStreamer */
gst_init (&argc, &argv);
loop = g_main_loop_new (NULL, FALSE);
/* check args */
if (argc != 2) {
g_print ("Usage: %s <filename>\n", argv[0]);
return -1;
}
/* create a new pipeline to hold the elements */
pipeline = gst_pipeline_new ("pipe");
bus = gst_pipeline_get_bus (GST_PIPELINE (pipeline));
gst_bus_add_watch (bus, my_bus_callback, NULL);
gst_object_unref (bus);
/* create file source and typefind element */
filesrc = gst_element_factory_make ("filesrc", "source");
g_object_set (G_OBJECT (filesrc), "location", argv[1], NULL);
typefind = gst_element_factory_make ("typefind", "typefinder");
g_signal_connect (typefind, "have-type", G_CALLBACK (cb_typefound), loop);
fakesink = gst_element_factory_make ("fakesink", "sink");
/* setup */
gst_bin_add_many (GST_BIN (pipeline), filesrc, typefind, fakesink, NULL);
gst_element_link_many (filesrc, typefind, fakesink, NULL);
gst_element_set_state (GST_ELEMENT (pipeline), GST_STATE_PLAYING);
g_main_loop_run (loop);
/* unset */
gst_element_set_state (GST_ELEMENT (pipeline), GST_STATE_NULL);
gst_object_unref (GST_OBJECT (pipeline));
return 0;
}
 

```
 
Sample output:
> 
./a.out Epoq-Lepidoptera.ogg
Media type application/ogg found, probability 100%
Got state-changed message
Got state-changed message
Got state-changed message
Got state-changed message
Got state-changed message
Got stream-status message
Got state-changed message
Got stream-status message
Got state-changed message
Got state-changed message
./a.out 02.mp4
Media type application/x-3gp, profile=(string)basic found, probability 100%
Got state-changed message
Got state-changed message
Got state-changed message
Got state-changed message
Got state-changed message
Got stream-status message
Got state-changed message
Got stream-status message
Got state-changed message
Got state-changed message
Got async-done message
 

 
Hi,
I am trying to build a basic media player which will paly any format of audio.
I used gstreamer0.10 frame work and used some sample program which is given in 17th chapter of programmer reference manual.
[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/manual.pdf](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/manual.pdf)
 
but when i execute the program it just showing the set of messages and thats all.
I am using the code and sample out above.
 
Please help.

---

