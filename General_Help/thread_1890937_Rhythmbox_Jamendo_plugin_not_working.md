---
title: "Rhythmbox Jamendo plugin not working"
date: 2011-12-04
forum: General Help
---

### Post by FallenUnia on 2011-12-04
Hey all,

I just ditched Banshee for Rhythmbox and installed its Jamendo plugin. However, it stays stuck at the Jamendo introduction screen thingy.. I can't browse nor play music. From terminal, I got this output:

```

Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/rb/Loader.py", line 177, in check_for_update
    lfi = lf.query_info(Gio.FILE_ATTRIBUTE_TIME_MODIFIED, Gio.FileQueryInfoFlags.NONE, None)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Fout bij het benaderen van bestand ‘/home/jente/.cache/rhythmbox/jamendo/dbdump.xml’: Bestand of map bestaat niet
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 126, in do_selected
    self.__update_catalogue()
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 233, in __update_catalogue
    self.__catalogue_check.check_for_update(self.__local_catalogue_path, jamendo_song_info_uri, update_cb)
  File "/usr/lib/rhythmbox/plugins/rb/Loader.py", line 184, in check_for_update
    self.callback(True, *self.args)
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 228, in update_cb
    self.__download_catalogue()
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 222, in __download_catalogue
    self.__catalogue_loader.get_url_chunks(jamendo_song_info_uri, 4*1024, True, self.__download_catalogue_chunk_cb, out)
  File "/usr/lib/rhythmbox/plugins/rb/Loader.py", line 134, in get_url_chunks
    raise Exception("rb.ChunkLoader not implemented yet")
Exception: rb.ChunkLoader not implemented yet

```

Can someone help me fix this?

---

