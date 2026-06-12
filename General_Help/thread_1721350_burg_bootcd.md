---
title: "burg bootcd"
date: 2011-04-04
forum: General Help
---

### Post by ylafont on 2011-04-04
[RIGHT]   	 	 	 	[/RIGHT]
p { margin-bottom: 0.08in; }a:link {  }  Burg – Boot-CD – Has anyone done this?
 

 At first  and the easiest method, I thought was to  make a burg floppy disk and use it as an image to boot a CD, however when I do that, I can boot, but I cannot see the files on the CD, except the image of the floppy.  Is there a command withing burg/grub that will allow access to the files on the CDROM?   
 

 After that I thought  I could use BURG-MKRESCUE -o /name of ISO file  just like you can with GRUB-MKRESCUE -o/name of ISO file.  BURG-MKRESCUE complains about the “-o” option and  list the following as available options
 

 **burg-mkrescue  -o /mnt/hgfs/C/test.iso**  
 Unrecognized option `-o' 
 Usage: /usr/bin/burg-mkrescue [OPTION] SOURCE... 
 Make GRUB rescue image. 
  
   -h, --help              print this message and exit 
   -v, --version           print the version information and exit 
   --modules=MODULES       pre-load specified modules MODULES 
   --output=FILE           save output in FILE [required] 
  
 /usr/bin/burg-mkrescue generates a bootable rescue image with specified source files or directories. 
  
 Report bugs to <[EMAIL="bug-grub@gnu.org"]bug-grub@gnu.org[/EMAIL]>. 
 

 when I use the “--output-” option  tells me the  following”
 

 --output=/mnt/hgfs/C/test.iso  
 Enabling BIOS support ... 
 Target format not specified (use the -O option). 
 Try `grub-mkimage --help' for more information
 

 and finally when I give the option is wants it tell me the following
 

 **burg-mkrescue  --output=/mnt/hgfs/C/test.iso  --format=i386-pc **
 Unrecognized option `--format=i386-pc' 
 Usage: /usr/bin/burg-mkrescue [OPTION] SOURCE... 
 Make GRUB rescue image. 
  
   -h, --help              print this message and exit 
   -v, --version           print the version information and exit 
   --modules=MODULES       pre-load specified modules MODULES 
   --output=FILE           save output in FILE [required] 
  
 /usr/bin/burg-mkrescue generates a bootable rescue image with specified source files or directories. 
  
 

 Does any have any ideas on how I can accomplish this?

---

