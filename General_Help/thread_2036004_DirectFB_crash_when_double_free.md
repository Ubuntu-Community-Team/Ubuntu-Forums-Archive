---
title: "DirectFB crash when double free"
date: 2012-07-31
forum: General Help
---

### Post by lsmgeb89 on 2012-07-31
I have found that my application with DirectFB will crash when program quits.
It will caught signal 11.
It seems that my problem is the same as [https://bugs.launchpad.net/ubuntu/+source/directfb/+bug/691440](https://bugs.launchpad.net/ubuntu/+source/directfb/+bug/691440)
I use a simple test program(line.c) to test it in another virtual machine (Ubuntu 11.04) in VMware Workstation.
```

/* line.c */
#include <stdio.h>
#include <unistd.h>
#include <directfb.h>
static IDirectFB *dfb = NULL;
static IDirectFBSurface *primary = NULL;
static int screen_width = 0;
static int screen_height = 0;
#define DFBCHECK(x...)                                               \
  {                                                                    \
        DFBResult err = x;                                            \
        if (err != DFB_OK)                                            \
        {                                                            \
            fprintf(stderr, "%s. <%d>:\n\t", __FILE__, __LINE__);    \
             DirectFBErrorFatal( #x, err );                         \
        }                                                             \
    }
int main (int argc, char **argv)
{
    DFBSurfaceDescription dsc;
    DFBCHECK(DirectFBInit(&argc, &argv));
    DFBCHECK(DirectFBCreate(&dfb));
    //DFBCHECK(dfb->SetCooperativeLevel(dfb, DFSCL_FULLSCREEN));
    dsc.flags = DSDESC_CAPS;
    dsc.caps = DSCAPS_PRIMARY | DSCAPS_FLIPPING;
    DFBCHECK(dfb->CreateSurface(dfb, &dsc, &primary));
    DFBCHECK(primary->GetSize(primary, &screen_width, &screen_height));
    DFBCHECK(primary->FillRectangle (primary, 0, 0, screen_width, screen_height));
    DFBCHECK(primary->SetColor (primary, 0x80, 0x80, 0xff, 0xff));
    DFBCHECK(primary->DrawLine (primary, 0, screen_height / 2, screen_width - 1, screen_height / 2));
    DFBCHECK(primary->Flip (primary, NULL, 0));
    sleep(5);
    primary->Release( primary );
    dfb->Release(dfb);
    return 23;
}

```It will not crash in my Virtual Machine.
From the log, I found the difference that DirectFB will not crash when it is using XShm.
This could be verified by [http://www.mail-archive.com/directfb-dev@directfb.org/msg08039.html](http://www.mail-archive.com/directfb-dev@directfb.org/msg08039.html)
So how can I let DirectFB to use XShm?
Ubuntu version: 12.04
Laptop: ThinkPad T61
Graphic Card: Nvidia Quadro NVS 140M
Nvidia Driver version: 295.49
Thanks a lot!

---

### Post by lsmgeb89 on 2012-08-10
Nobody knows how to resolve this problem?

---

