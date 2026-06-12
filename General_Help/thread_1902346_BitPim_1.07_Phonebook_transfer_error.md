---
title: "BitPim 1.07 Phonebook transfer error"
date: 2011-12-30
forum: General Help
---

### Post by Bill Gates Foundation on 2011-12-30
Ubuntu 11.10
BitPim 1.07 w/ updates
Dare LG9700vx phone

I have gotton ringtones, text messages, and wallpaper to transfer.  Phonebook gives me an error.  Everything works properly on my XP machine.
 



[COLOR=Blue]> BitPim version: 1.0.7-Debian
An unexpected exception has occurred.
Please see the help for details on what to do.

Traceback (most recent call last):
  File "/usr/share/bitpim/code/gui.py", line 284, in run
    res=call()
  File "/usr/share/bitpim/code/gui.py", line 159, in __call__
    return apply(self.method, self.args+args, d)
  File "/usr/share/bitpim/code/gui.py", line 1906, in getdata
    i[1](results)
  File "/usr/share/bitpim/code/phones/com_lgvx8550.py", line 141, in getphonebook
    if not pb_entry.valid():
  File "/usr/share/bitpim/code/phones/p_lgvx8550.py", line 607, in valid
    return self.entry_tag==PB_ENTRY_SOR and ord(self.name[0]) != 0xff
IndexError: string index out of range

Variables by last 8 frames, innermost last

Frame run in /usr/share/bitpim/code/gui.py at line 277
       resultcb =  <gui.Callback instance at 0xa5db50c>
            res =  None
           self =  <WorkerThread(BitPim helper, started daemon -1269245072)>
           item =  (<gui.Request instance at 0xb67a10c>, <gui.Callback instance at 0xa5db50c>)
           call =  <gui.Request instance at 0xb67a10c>
             ex =  IndexError('string index out of range',)
              e =  IndexError('string index out of range',)
          first =  0

Frame __call__ in /usr/share/bitpim/code/gui.py at line 159
           self =  <gui.Request instance at 0xb67a10c>
           args =  ()
              d =  Keys []
                   {}
         kwargs =  Keys []
                   {}

Frame getdata in /usr/share/bitpim/code/gui.py at line 1906
          count =  1
              i =  (<bound method GetPhoneDialog.GetPhoneBookSetting of <guiwidgets.GetPhoneDialog;
           self =  <WorkerThread(BitPim helper, started daemon -1269245072)>
            req =  <guiwidgets.GetPhoneDialog; proxy of <Swig Object of type 'wxDialog *' at 0xb1b9
       willcall =  [(<bound method GetPhoneDialog.GetPhoneBookSetting of <guiwidgets.GetPhoneDialog
        results =  Keys ['groups', 'ringtone-index', 'sync', 'uniqueserial', 'wallpaper-index']
                   {'sync': {'phonebook': 'MERGE'}, 'wallpaper-index': {100: {'origin': 'images(sd)
           sync =  Keys ['phonebook']
                   {'phonebook': 'MERGE'}
             st =  0
           todo =  [(<bound method WorkerThread.rebootcheck of <WorkerThread(BitPim helper, started

Frame getphonebook in /usr/share/bitpim/code/phones/com_lgvx8550.py at line 141
          pbook =  Keys [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
                   {0: {'serials': [{'serial2': 1, 'serial1': 1, 'sourcetype': 'lgvx9700', 'sourceu
        _rt_ids =  Keys []
                   {}
        _wp_ids =  Keys []
                   {}
        _speeds =  Keys [0, 1, 1000]
                   {1000: {6: 1}, 0: {1: 97}, 1: {1: 98}}
           self =  <phones.com_lgvx9700.Phone object at 0xb672cec>
           _cnt =  11
       pb_entry =  <phones.p_lgvx8550.pbfileentry object at 0xbba7dcc>
     pb_numbers =  <phones.p_lgvx8550.pnfile object at 0xb2ace7ac>
     ring_pathf =  <phones.p_lgvx8550.PathIndexFile object at 0xb22b980c>
         result =  Keys ['groups', 'ringtone-index', 'sync', 'uniqueserial', 'wallpaper-index']
                   {'sync': {'phonebook': 'MERGE'}, 'wallpaper-index': {100: {'origin': 'images(sd)
    picid_pathf =  <phones.p_lgvx8550.PathIndexFile object at 0xb22b986c>
     pb_entries =  <phones.p_lgvx8550.pbfile object at 0xc33c46c>
          _ices =  Keys [4, 9, 12]
                   {12: 1, 4: 0, 9: 2}

Frame valid in /usr/share/bitpim/code/phones/p_lgvx8550.py at line 607
           self =  <phones.p_lgvx8550.pbfileentry object at 0xbba7dcc>[/COLOR]

---

