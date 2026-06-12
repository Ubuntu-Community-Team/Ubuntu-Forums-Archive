---
title: "Installing driver for TIUSB3410 and eZ430-RF2500 (MSP430)"
date: 2009-06-28
forum: General Help
---

### Post by amoya on 2009-06-28
Hello,

I'm going crazy to install the MSP430 driver in UBUNTU 8.04 hardy and kernel
2.6.24-23.

in /lib/modules/<<kernel>>/kernel/drivers/usb/serial i have a driver named
ti_usb_3410_5052.ko but seems not work correctly.
i follow this steps:

1. I download the linux-2.6.24 source from kernel.org.
2. I untar this in /usr/src.
3  I enter directory /usr/src/linux-2.6.24
4  I modify the ti_usb_3410_5052.c as follows:

static struct usb_serial_driver ti_1port_device = {
    .driver = {
        .owner        = THIS_MODULE,
        .name        = "ti_usb_3410_5052_1",
    },
    .description        = "TI USB 3410 1 port adapter",
    .usb_driver        = &ti_usb_driver,
    .id_table        = ti_id_table_3410,
   * .num_interrupt_in    = NUM_DONT_CARE,**
    .num_bulk_in        = NUM_DONT_CARE,*
    .num_bulk_out        = 1,
    .num_ports        = 1,
    .attach            = ti_startup,

and:

/* 3410 must be reset, 5052 resets itself */
        if (tdev->td_is_3410) {
            msleep_interruptible(100);
            usb_reset_device(dev);
        }

       * status = 0x01e;*
        goto free_tdev;
    }

    /* the second configuration must be set (in sysfs by hotplug script) */
    if (dev->actconfig->desc.bConfigurationValue == TI_BOOT_CONFIG) {
       * (void) usb_driver_set_configuration(dev, TI_ACTIVE_CONFIG);**
        status = 0xa1b;*
        goto free_tdev;
    }

5. I run Make.
6. I copy the ti_usb_3410_5052.ko from
/usr/src/linux-2.6.24/drivers/usb/serial to
/lib/modules/<<kernel>>/kernel/drivers/usb/serial/ti_usb_3410_5052.ko.
7. I register the new module doing: sudo modprobe ti_usb_3410_5052

is it correct? i missed more steps?

But...I don't know if there's a rule or a script to tell the system to read
the driver when i plug the mote.

Do you know the correct steps to make it work in UBUNTU 8.04 with kernel
2.6.24-23?.

Thank you in advance.

Aldo

---

