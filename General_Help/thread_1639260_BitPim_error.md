---
title: "BitPim error"
date: 2010-12-06
forum: General Help
---

### Post by joelstitch on 2010-12-06
I am trying to get some info from my LG-VN250 into BitPim but I am getting some errors. I had to set it up in BitPim as a LG-VX8560 (chocolate 3) because the LG-VN250 is not listed in BitPim and I read that using the LG-VX8560 should work. I am able to get some info into BitPim but nt the Phonebook which is what I need to get. This is the error Im getting:

> BitPim version: 1.0.6-Debian
An unexpected exception has occurred.
Please see the help for details on what to do.

Traceback (most recent call last):
  File "/usr/share/bitpim/code/gui.py", line 284, in run
    res=call()
  File "/usr/share/bitpim/code/gui.py", line 159, in __call__
    return apply(self.method, self.args+args, d)
  File "/usr/share/bitpim/code/gui.py", line 1913, in getdata
    i[1](results)
  File "/usr/share/bitpim/code/phones/com_lgvx8550.py", line 141, in getphonebook
    if not pb_entry.valid():
  File "/usr/share/bitpim/code/phones/p_lgvx8550.py", line 607, in valid
    return self.entry_tag==PB_ENTRY_SOR and ord(self.name[0]) != 0xff
IndexError: string index out of range

Variables by last 8 frames, innermost last

Frame run in /usr/share/bitpim/code/gui.py at line 277
       resultcb =  <gui.Callback instance at 0x445e368>
            res =  None
           self =  <WorkerThread(BitPim helper, started daemon 139878861322000)>
           item =  (<gui.Request instance at 0x445e4d0>, <gui.Callback instance at 0x445e368>)
           call =  <gui.Request instance at 0x445e4d0>
             ex =  IndexError('string index out of range',)
              e =  IndexError('string index out of range',)
          first =  0

Frame __call__ in /usr/share/bitpim/code/gui.py at line 159
           self =  <gui.Request instance at 0x445e4d0>
           args =  ()
              d =  Keys []
                   {}
         kwargs =  Keys []
                   {}

Frame getdata in /usr/share/bitpim/code/gui.py at line 1913
          count =  1
              i =  (<bound method GetPhoneDialog.GetPhoneBookSetting of <guiwidgets.GetPhoneDialog;
           self =  <WorkerThread(BitPim helper, started daemon 139878861322000)>
            req =  <guiwidgets.GetPhoneDialog; proxy of <Swig Object of type 'wxDialog *' at 0x3549
       willcall =  [(<bound method GetPhoneDialog.GetPhoneBookSetting of <guiwidgets.GetPhoneDialog
        results =  Keys ['groups', 'ringtone-index', 'sync', 'uniqueserial', 'wallpaper-index']
                   {'sync': {'phonebook': 'MERGE'}, 'wallpaper-index': {100: {'origin': 'images', '
           sync =  Keys ['phonebook']
                   {'phonebook': 'MERGE'}
             st =  0
           todo =  [(<bound method WorkerThread.rebootcheck of <WorkerThread(BitPim helper, started

Frame getphonebook in /usr/share/bitpim/code/phones/com_lgvx8550.py at line 141
          pbook =  Keys []
                   {}
        _rt_ids =  Keys []
                   {}
        _wp_ids =  Keys [u'mmc1/my_pix/DSC03516.JPG']
                   {u'mmc1/my_pix/DSC03516.JPG': u'DSC03516.JPG'}
        _speeds =  Keys [1000]
                   {1000: {6: 1}}
           self =  <phones.com_lgvx8560.Phone object at 0x3f6f450>
           _cnt =  0
       pb_entry =  <phones.p_lgvx8550.pbfileentry object at 0x4473b50>
     pb_numbers =  <phones.p_lgvx8550.pnfile object at 0x7f3810a9ef50>
     ring_pathf =  <phones.p_lgvx8550.PathIndexFile object at 0x2ebb610>
         result =  Keys ['groups', 'ringtone-index', 'sync', 'uniqueserial', 'wallpaper-index']
                   {'sync': {'phonebook': 'MERGE'}, 'wallpaper-index': {100: {'origin': 'images', '
    picid_pathf =  <phones.p_lgvx8550.PathIndexFile object at 0x7f3811ba2b10>
     pb_entries =  <phones.p_lgvx8550.pbfile object at 0x4473bd0>
          _ices =  Keys [69]
                   {69: 0}

Frame valid in /usr/share/bitpim/code/phones/p_lgvx8550.py at line 607
           self =  <phones.p_lgvx8550.pbfileentry object at 0x4473b50>


---

### Post by 73ckn797 on 2010-12-06
I have not used Bitpim in a while but seem to recall I had to run it as root for it to work properly. In a terminal enter: ```
sudo bitpim
```

---

### Post by joelstitch on 2010-12-06
> **73ckn797 said:**
> I have not used Bitpim in a while but seem to recall I had to run it as root for it to work properly. In a terminal enter: ```
sudo bitpim
```

I'm still getting the error:(

---

