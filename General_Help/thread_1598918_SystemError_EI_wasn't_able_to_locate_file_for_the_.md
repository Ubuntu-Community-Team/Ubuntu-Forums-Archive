---
title: "SystemError: E:I wasn't able to locate file for the mysqmail package. This might mean"
date: 2010-10-17
forum: General Help
---

### Post by mendoh on 2010-10-17
Hi everybody!

I was wondering if anyone could help with the following error I am getting from aptdaemon:

[B]Traceback (most recent call last):
File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
return self._simulate_helper(trans, status_path)
File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
return depends, status, self._cache.required_download, \
File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the mysqmail package. This might mean you need to manually fix this package.[/B]

I am currently _unable to install any new software_ because of the above error and it all came up when I tried to install (without success) mysqlmail on my Ubuntu.

Thanks a lot in advance

Mendoh

---

