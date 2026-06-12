---
title: "error running gpodder"
date: 2012-06-14
forum: General Help
---

### Post by rd1381 on 2012-06-14
hi
i installed gpodder and it worked fine.
then yesterrday out of nowhere it didn't run anymore ,so i checked and it said this error:
```

glib.GError: Couldn't recognize the image file format for file '/usr/share/gpodder/podcast-3.png'

```
i tried deleting and re-installing gpodder and even restarting my laptop but the error persists.
any idea how this can be fixed?

---

### Post by radu_radu on 2012-06-15
I just got the same problem like you, and here is my console output:

```
Traceback (most recent call last):
  File "/usr/bin/gpodder", line 218, in <module>
    gui.main(options)
  File "/usr/lib/pymodules/python2.7/gpodder/gui.py", line 4256, in main
    gp = gPodder(bus_name, config)
  File "/usr/lib/pymodules/python2.7/gpodder/gui.py", line 179, in __init__
    BuilderWidget.__init__(self, None)
  File "/usr/lib/pymodules/python2.7/gpodder/gtkui/interface/common.py", line 56, in __init__
    GtkBuilderWidget.__init__(self, gpodder.ui_folders, gpodder.textdomain, **kwargs)
  File "/usr/lib/pymodules/python2.7/gpodder/gtkui/base.py", line 70, in __init__
    self.new()
  File "/usr/lib/pymodules/python2.7/gpodder/gui.py", line 490, in new
    self.update_feed_cache(force_update=False)
  File "/usr/lib/pymodules/python2.7/gpodder/gui.py", line 3023, in update_feed_cache
    self.update_podcast_list_model(select_url=select_url_afterwards)
  File "/usr/lib/pymodules/python2.7/gpodder/gui.py", line 2504, in update_podcast_list_model
    self.podcast_list_model.set_channels(self.db, self.config, self.channels)
  File "/usr/lib/pymodules/python2.7/gpodder/gtkui/model.py", line 737, in set_channels
    iter = self.append(channel_to_row(channel, True))
  File "/usr/lib/pymodules/python2.7/gpodder/gtkui/model.py", line 724, in channel_to_row
    self._get_cover_image(channel, add_overlay), '', True, True, True, \
  File "/usr/lib/pymodules/python2.7/gpodder/gtkui/model.py", line 683, in _get_cover_image
    pixbuf = self._cover_downloader.get_cover(channel, avoid_downloading=True)
  File "/usr/lib/pymodules/python2.7/gpodder/gtkui/services.py", line 122, in get_cover
    (url, pixbuf) = self.__get_cover(channel, custom_url, False, avoid_downloading)
  File "/usr/lib/pymodules/python2.7/gpodder/gtkui/services.py", line 155, in __get_cover
    return (channel.url, self.get_default_cover(channel))
  File "/usr/lib/pymodules/python2.7/gpodder/gtkui/services.py", line 151, in get_default_cover
    return gtk.gdk.pixbuf_new_from_file(filename)
glib.GError: Couldn't recognize the image file format for file '/usr/share/gpodder/podcast-3.png'
```

---

