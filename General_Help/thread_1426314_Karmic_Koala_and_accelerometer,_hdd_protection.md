---
title: "Karmic Koala and accelerometer, hdd protection"
date: 2010-03-10
forum: General Help
---

### Post by elempe on 2010-03-10
Hello,

I'm using FSC Lifebook S series, to be more specific S7210. I know from specs and from Win that it contains onboard accelerometer, in Win Vista it works perfectly, with FSC supplied "Motion sensor utility" it protects hard disk from damage during sudden shakes of notebook. 

The question is - i couldn't anyhow find any note in Ubuntu that it is recognized and is used as it should be. So I'm wondering is it done automatically or it is not used at all?
Pleas could anyone help me to get clear this case. If it is working is there any way to check some status of it, or if it isn't how to get it to protect hdd?

Thanks and cheers!

---

### Post by coldraven on 2010-03-10
I was wondering the same thing with this Compaq 6715b laptop. The only info I have found is that if you install the game Neverball you can steer the ball by tilting your laptop!
So the accelerometer is being detected but AFAIK it is not protecting the hard drive.
Maybe someone else knows better. I live in hope!

p.s. Neverball is in the repository and is quite addictive ;)

Just ran hwinfo and got this output

29: udi = '/org/freedesktop/Hal/devices/platform_lis3lv02d_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  info.capabilities = { 'input' }
  input.device = '/dev/input/event6'
  input.product = 'ST LIS3LV02DL Accelerometer'
  info.category = 'input'
  linux.device_file = '/dev/input/event6'
  info.subsystem = 'input'
  info.product = 'ST LIS3LV02DL Accelerometer'
  linux.sysfs_path = '/sys/devices/platform/lis3lv02d/input/input6/event6'
  info.parent = '/org/freedesktop/Hal/devices/platform_lis3lv02d'
  input.originating_device = '/org/freedesktop/Hal/devices/platform_lis3lv02d'
  info.udi = '/org/freedesktop/Hal/devices/platform_lis3lv02d_logicaldev_input'

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
  N: Name="ST LIS3LV02DL Accelerometer"
  P: Phys=lis3lv02d/input0
  S: Sysfs=/devices/platform/lis3lv02d/input/input6
  U: Uniq=
  H: Handlers=event6 js0 
  B: EV=9
  B: ABS=7

bus = 25, name = ST LIS3LV02DL Accelerometer
  handlers = event6 js0
  abs = 0000000000000007
  mouse buttons = 0
  mouse wheels = 0

P: /devices/platform/lis3lv02d/input/input6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/lis3lv02d/input/input6
  E: PRODUCT=19/0/0/0
  E: NAME="ST LIS3LV02DL Accelerometer"
  E: PHYS="lis3lv02d/input0"
  E: EV==9
  E: ABS==7
  E: MODALIAS=input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw
  E: SUBSYSTEM=input

Now what that all means is beyond me!
Where are the experts?

---

