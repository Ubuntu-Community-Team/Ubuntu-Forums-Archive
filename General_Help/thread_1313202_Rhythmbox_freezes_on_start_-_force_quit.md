---
title: "Rhythmbox freezes on start - force quit"
date: 2009-11-03
forum: General Help
---

### Post by Number13 on 2009-11-03
i did the upgrade to 9.10 :(xubuntu 9.10 64)

now Rhythmbox freezes when i try to play anything.
I have done a search and i cant find a solution.

```
@LinuX:~$ rhythmbox

** (rhythmbox:3522): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3522): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:3522): Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
Killed
```



 i have tried
```
sudo apt-get remove rhythmbox --purge
sudo apt-get install rhythmbox
```
that works temporarily. but if i close it and reopen it im back to square 1.

anybody?

---

### Post by kja999 on 2009-11-03
Not a solution, but rhythmbox does have a -d switch for debugging.
Try it and see what you get ..

---

### Post by joshd2189 on 2009-11-06
I'm having the exact same problem after upgrading to 9.10 from 9.04.

sometimes i am able to get rhythmbox to start playing a song, but even then it is very choppy until it freezes altogether.  anyways, here is what happened when i ran rhythmbox -d.  

The timer kept scrolling forward, however the position in the file (i think- it's bolded) remained constant:
> 
(00:02:27) [0x1e8e040] [tick_cb] rb-shell-player.c:3513: tick: [file:///XX.mp3, **107430187499:242000000000**(0)]

The following outputs occurred periodically amongst the stream of the above output:
> (00:08:56) [0x13ad040] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:758: No username set

> (00:10:06) [0x13ad040] [rhythmdb_read_enter] rhythmdb.c:1223: counter: 1
(00:10:06) [0x13ad040] [rhythmdb_read_enter] rhythmdb.c:1223: counter: 2
(00:10:06) [0x2b61f90] [query_thread_main] rhythmdb.c:4098: entering query thread
(00:10:06) [0x2b61f90] [rhythmdb_query_internal] rhythmdb.c:4075: doing query
(00:10:06) [0x2b61f90] [do_query_recurse] rhythmdb-tree.c:2243: doing recursive query, 1 conjunctions
(00:10:06) [0x2bb3eb0] [query_thread_main] rhythmdb.c:4098: entering query thread
(00:10:06) [0x2bb3eb0] [rhythmdb_query_internal] rhythmdb.c:4075: doing query
(00:10:06) [0x2bb3eb0] [do_query_recurse] rhythmdb-tree.c:2243: doing recursive query, 1 conjunctions
(00:10:06) [0x2b61f90] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2023: adding 445 entries
(00:10:06) [0x2b61f90] [rhythmdb_query_internal] rhythmdb.c:4081: completed
(00:10:06) [0x13ad040] [idle_process_update] rhythmdb-query-model.c:1065: inserting 445 rows
(00:10:06) [0x13ad040] [rhythmdb_process_one_event] rhythmdb.c:2637: processing RHYTHMDB_EVENT_QUERY_COMPLETE
(00:10:06) [0x13ad040] [rhythmdb_read_leave] rhythmdb.c:1237: counter: 1
(00:10:06) [0x13ad040] [rhythmdb_process_one_event] rhythmdb.c:2630: processing RHYTHMDB_EVENT_THREAD_EXITED
(00:10:06) [0x2bb3eb0] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2023: adding 50 entries
(00:10:06) [0x2bb3eb0] [rhythmdb_query_internal] rhythmdb.c:4081: completed
(00:10:06) [0x13ad040] [idle_process_update] rhythmdb-query-model.c:1065: inserting 50 rows
(00:10:06) [0x13ad040] [rhythmdb_process_one_event] rhythmdb.c:2637: processing RHYTHMDB_EVENT_QUERY_COMPLETE
(00:10:06) [0x13ad040] [rhythmdb_read_leave] rhythmdb.c:1237: counter: 0
(00:10:06) [0x13ad040] [rhythmdb_process_one_event] rhythmdb.c:2630: processing RHYTHMDB_EVENT_THREAD_EXITED


---

### Post by tazir on 2009-11-07
After upgrading to U?buntu 9.10, Rhythmbox is work, but show error msg:
rhythmbox

** (rhythmbox:25395): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:25395): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:25395): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(rhythmbox:25395): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(rhythmbox:25395): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

---

