---
title: "What do these error messages mean?"
date: 2010-12-16
forum: General Help
---

### Post by cysin on 2010-12-16
I am using ubuntu 10.0.4 TLS, and this is my main board info: [http://www.made-in-china.com/showroom/geshem/product-detailbqfJOksvrXcn/China-Mainboard-ITX-WN45A-D.html](http://www.made-in-china.com/showroom/geshem/product-detailbqfJOksvrXcn/China-Mainboard-ITX-WN45A-D.html)

These error messages were from /var/log/messages

```
Dec 17 09:46:53 my-desktop kernel: [ 1080.890084] i915          D 0000000000000000     0   595      2 0x00000000
Dec 17 09:46:53 my-desktop kernel: [ 1080.890096]  ffff880030257d40 0000000000000046 0000000000015bc0 0000000000015bc0
Dec 17 09:46:53 my-desktop kernel: [ 1080.890107]  ffff880030b53178 ffff880030257fd8 0000000000015bc0 ffff880030b52dc0
Dec 17 09:46:53 my-desktop kernel: [ 1080.890117]  0000000000015bc0 ffff880030257fd8 0000000000015bc0 ffff880030b53178
Dec 17 09:46:53 my-desktop kernel: [ 1080.890127] Call Trace:
Dec 17 09:46:53 my-desktop kernel: [ 1080.890148]  [<ffffffff81542907>] __mutex_lock_slowpath+0xf7/0x180
Dec 17 09:46:53 my-desktop kernel: [ 1080.890161]  [<ffffffff810578b0>] ? finish_task_switch+0x50/0xe0
Dec 17 09:46:53 my-desktop kernel: [ 1080.890169]  [<ffffffff815427eb>] mutex_lock+0x2b/0x50
Dec 17 09:46:53 my-desktop kernel: [ 1080.890207]  [<ffffffffa0110add>] i915_gem_retire_work_handler+0x3d/0xa0 [i915]
Dec 17 09:46:53 my-desktop kernel: [ 1080.890231]  [<ffffffffa0110aa0>] ? i915_gem_retire_work_handler+0x0/0xa0 [i915]
Dec 17 09:46:53 my-desktop kernel: [ 1080.890243]  [<ffffffff8107f9a7>] run_workqueue+0xc7/0x1a0
Dec 17 09:46:53 my-desktop kernel: [ 1080.890252]  [<ffffffff8107fb23>] worker_thread+0xa3/0x110
Dec 17 09:46:53 my-desktop kernel: [ 1080.890261]  [<ffffffff81084570>] ? autoremove_wake_function+0x0/0x40
Dec 17 09:46:53 my-desktop kernel: [ 1080.890270]  [<ffffffff8107fa80>] ? worker_thread+0x0/0x110
Dec 17 09:46:53 my-desktop kernel: [ 1080.890278]  [<ffffffff810841f6>] kthread+0x96/0xa0
Dec 17 09:46:53 my-desktop kernel: [ 1080.890287]  [<ffffffff810131ea>] child_rip+0xa/0x20
Dec 17 09:46:53 my-desktop kernel: [ 1080.890296]  [<ffffffff81084160>] ? kthread+0x0/0xa0
Dec 17 09:46:53 my-desktop kernel: [ 1080.890303]  [<ffffffff810131e0>] ? child_rip+0x0/0x20
Dec 17 10:08:53 my-desktop kernel: [ 2400.890080] i915          D 0000000000000000     0   595      2 0x00000000
Dec 17 10:08:53 my-desktop kernel: [ 2400.890092]  ffff880030257d40 0000000000000046 0000000000015bc0 0000000000015bc0
Dec 17 10:08:53 my-desktop kernel: [ 2400.890103]  ffff880030b53178 ffff880030257fd8 0000000000015bc0 ffff880030b52dc0
Dec 17 10:08:53 my-desktop kernel: [ 2400.890113]  0000000000015bc0 ffff880030257fd8 0000000000015bc0 ffff880030b53178
Dec 17 10:08:53 my-desktop kernel: [ 2400.890122] Call Trace:
Dec 17 10:08:53 my-desktop kernel: [ 2400.890143]  [<ffffffff81542907>] __mutex_lock_slowpath+0xf7/0x180
Dec 17 10:08:53 my-desktop kernel: [ 2400.890156]  [<ffffffff810578b0>] ? finish_task_switch+0x50/0xe0
Dec 17 10:08:53 my-desktop kernel: [ 2400.890164]  [<ffffffff815427eb>] mutex_lock+0x2b/0x50
Dec 17 10:08:53 my-desktop kernel: [ 2400.890202]  [<ffffffffa0110add>] i915_gem_retire_work_handler+0x3d/0xa0 [i915]
Dec 17 10:08:53 my-desktop kernel: [ 2400.890226]  [<ffffffffa0110aa0>] ? i915_gem_retire_work_handler+0x0/0xa0 [i915]
Dec 17 10:08:53 my-desktop kernel: [ 2400.890237]  [<ffffffff8107f9a7>] run_workqueue+0xc7/0x1a0
Dec 17 10:08:53 my-desktop kernel: [ 2400.890246]  [<ffffffff8107fb23>] worker_thread+0xa3/0x110
Dec 17 10:08:53 my-desktop kernel: [ 2400.890256]  [<ffffffff81084570>] ? autoremove_wake_function+0x0/0x40
Dec 17 10:08:53 my-desktop kernel: [ 2400.890265]  [<ffffffff8107fa80>] ? worker_thread+0x0/0x110
Dec 17 10:08:53 my-desktop kernel: [ 2400.890273]  [<ffffffff810841f6>] kthread+0x96/0xa0
Dec 17 10:08:53 my-desktop kernel: [ 2400.890283]  [<ffffffff810131ea>] child_rip+0xa/0x20
Dec 17 10:08:53 my-desktop kernel: [ 2400.890291]  [<ffffffff81084160>] ? kthread+0x0/0xa0

```

---

