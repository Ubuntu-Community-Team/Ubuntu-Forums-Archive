---
title: "Software Download Centre Error/Problem - Help Needed"
date: 2011-01-27
forum: General Help
---

### Post by CollyMcK on 2011-01-27
Hi Guys,

I am just coming back to Linux - studied it in Uni for a module but havent used it in a while. I got Ubuntu running fine on my Sony Vaio laptop. I went to a wesite to find ten best programs to download. I ran into an error with the first and tried to do a kill on the get/apt process i think it was. I then tried to kill some root processes and tried a restart but my software centre is still not working correctly.

I have attached a print screen of the message I am getting. Can anyone help me resolve this. If not would my best option be to format the partition i put linux on and re-install it as I really want to be using it.

Thanks for any help.

Traceback (most recent call last):
File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
return self._simulate_helper(trans, status_path)
File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
return depends, status, self._cache.required_download, \
File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

---

