---
title: "Can't i set an alias to the Trash folder"
date: 2009-11-06
forum: General Help
---

### Post by emigrant on 2009-11-06
hi all,
can't i set an alias in my bash file to the Trash folder as follows:
so that can move to Trash without using rm.

```
alias Trash= "/home/emigrant/.local/share/Trash/files"
```

---

### Post by emigrant on 2009-11-06
if i do like that the terminal give me this error:

```

bash: alias: /home/emigrant/.local/share/Trash/files: not found

```

---

### Post by alphaniner on 2009-11-06
You want to put stuff in the trash through the terminal?  I don't think it's practical to do that with just an alias.  I think you'd want to run a small script.

The alias you have is essentially trying to run /home/emigrant/.local/share/Trash/files.

---

### Post by benj1 on 2009-11-06
you dont really want to do it like that because trash saves details of when and where something was deleted

heres a script i wrote to do the job
```

#!/usr/bin/env python
#
#       bin.py
#       
#       Copyright 2009 Ben Holroyd <ben@ben-desktop>
#       
#       This program is free software; you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation; either version 3 of the License, or
#       (at your option) any later version.
#       
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#       
#       You should have received a copy of the GNU General Public License
#       along with this program; if not, write to the Free Software
#       Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
#       MA 02110-1301, USA.

# pretty much compatible with gnome trashbin although everything is sent to main
# trashbin in ~/.local/share/Trash/files rather than devices local trash file in
# i prefer this behaviour but it is not compatible with that stipulated in the
# freedesktop.org trashcan specification. 

import os, sys

class Path():
	""" deals with all things todo with paths... obviously"""
	import os
	def __init__(self ):
		self.home = os.environ['HOME']
		self.delete_path = self.home +'/.local/share/Trash/files' # join doesn't work
		self.info_path = self.home +'/.local/share/Trash/info'
		self.info_suffix = '.trashinfo'
		
	def filename (self,arg):
		return os.path.split(arg)[1]
		
	def path_sans_filename (self, arg):
		return os.path.split(arg)[0]
		
	def full_delete_path(self,arg):
		return os.path.join(self.delete_path,self.filename(arg)) 
		
	def full_info_path(self,arg):
		return os.path.join(self.info_path,self.filename(arg))+ self.info_suffix
		
	def path (self,arg):
		""" expands and cleans up path in every conceivable way."""
		return os.path.realpath(os.path.normpath(os.path.abspath(os.path.expanduser(arg))))
		
	def join (self,arg,arg2):
		return os.path.join(arg,arg2)
		
	def ls (self, dir):
		return os.listdir(dir)


def get_date():
	import datetime
	return datetime.datetime.now().strftime('%Y-%m-%dT%T')

def test_duplicate(filename, path):
	""" tests whether the file name already exists in the deleted file folder
	follows behaviour will add starting from 2 'prefix.x.suffix'."""
	index = 2
	filenametmp = filename
	while os.access(Path().join(path,filenametmp), os.F_OK) == True:
		if filename.find('.') != -1:
			filenametmp = filename[:filename.find('.')] + '.' + str(index) + filename[filename.find('.'):]
		else:
			filenametmp = filename + '.' + str(index) 
		index += 1
	return filenametmp
	

def trash_info(arg,filename, path):
	#split filename and path within this function?
	"""Writes files to the  trash info directory"""
	fullpath = path.path(arg)  #get full path for file to delete
	file = open(path.full_info_path(filename),'w')#get full path for new trashinfo file
	file.write('[Trash Info]\n')
	file.write('Path=%s\n' % fullpath)
	file.write('DeletionDate=%s\n' % get_date())
	file.close()

	
def main():
	from optparse import OptionParser
	path = Path()
	
	parser = OptionParser(
		version=" %prog V0.1-1  <holroyd.ben@gmail.com>",   
		description = "%prog - trash bin functionality for the commandline.",
		usage = "%prog [-dtrlv] [--viewbrief] [--delete] [--trash] [--restore]\n [--list] [--verbose] [--help] [--version]")
	parser.add_option("-d","--delete",action="store_true",dest="bldelete",default=False,help="permanently delete entries in the trash bin." )
	parser.add_option("-t","--trash", action="store_true" , dest="bltrash", default=False, help="send a file to the trash bin")
	parser.add_option("-r","--restore",action="store_true", dest="blrestore",default=False, help="restore a file from the trash bin")
	parser.add_option("-l","--list",action="store_true", dest="bllist",default=False, help="list files currently in the trash bin")
	parser.add_option("-v","--verbose" ,action="store_true",dest="blverbose",default=False,help="be verbose")
	parser.add_option("-i","--prompt" ,action="store_true",dest="blprompt",default=False,help="print confirmation prompt when deleting, trashing or restoring files")	
	global options
	(options, args) = parser.parse_args() #actually parse args
	
	if options.bldelete == False and options.bltrash == False and options.blrestore == False and options.bllist == False:
		if len(args) == 0:
			options.bllst = True
		else:
			options.bltrash = True
		
	if options.bldelete ^ options.bltrash ^ options.blrestore ^ options.bllist: pass
	else: parser.error("options can't be combined."); 
	
	
	if options.bltrash == True:
		from shutil import move
		for arg in args:
			if arg == '.' or arg == '..':
				sys.stderr.write(" error: '.' and '..' aren't valid filenames")
				pass
			if len(arg) > 0 and os.path.exists(path.path(arg)):
				#expands '~', sorts '..' etc and gives absolute, real path
				if options.blprompt == True:
					if raw_input("send '%s' to trash ?" % arg) in ['y','Y','yes','YES']: pass
					else: continue
				fullpath = path.path(arg)
				filename = path.filename(arg)
				filename = test_duplicate(filename, path.delete_path)
				move(fullpath, path.full_delete_path(filename))
				trash_info(arg, filename, path)
				if options.blverbose == True: 
					print "%s successfully sent to trash" % path.join(os.getcwd(),filename) 
					
	if options.bllist == True:
		for file in path.ls(path.delete_path):
			mode,inode,dev,nlink,uid,gid,size,atime,mtime,ctime = os.stat(path.full_delete_path(file))
			
			#get modified date
			from datetime import datetime
			date = datetime.fromtimestamp(mtime).strftime('%d-%m-%Y %H:%M')
			size = float(size)
            
            #format size
			size_index = 0
			while size > 1024 and size_index <= 4:
				size = size/1025
				size_index +=1
			size_names = ['B','K','M','G','T']
			size_index = size_names[size_index]
			
			#get name of owner
			import pwd
			username = pwd.getpwuid(uid).pw_name
			
			#get file type
			if os.path.isdir(path.full_delete_path(file)):
				filetype = 'd'
				blfiletype = True 
			elif os.path.isfile(path.full_delete_path(file)):
				filetype = 'f'
				blfiletype = False
			else: 
				filetype = '?'
				blfiletype = False
			
			#get deletion date
			fp = open(path.full_info_path(file),'r')
			dd = ''
			for lines in fp:
				if lines.startswith('DeletionDate'):
					dd = lines [13:-1]
					dd = dd.replace('T','  ')
			
			print " %s %s %.2f%s\t%s" % (filetype,username,size,size_index,dd), 
			if blfiletype == False: print file
			else: print "\033[34;02m%s\033[00;00m" % file #print file in colour
		
		if len(path.ls(path.delete_path)) == 0:
			sys.stderr.write('Trash is empty\n')
	
	if options.bldelete == True:
		def delete_entries(arg, path):
			import shutil
			try:
				if options.blprompt == True:
					if raw_input("permanently delete '%s'?" % arg) in ['y','Y','yes','YES']: pass
					else: return	
				if os.path.isdir(path.full_delete_path(arg)):
					shutil.rmtree(path.full_delete_path(arg))
				else:
					os.remove(path.full_delete_path(arg))
				os.remove(path.full_info_path(arg))
				if options.blverbose == True:
					print '%s deleted' % arg
			except:
					sys.stderr.write('problem deleting %s\n' % arg)		
		
		if len(args) == 0: #delete all if no argument
			for arg in path.ls(path.delete_path):
				delete_entries(arg, path)			
		else: 
			for arg in args:
				delete_entries(arg, path)

	
	if options.blrestore == True:
		 from shutil import move
		 for arg in args:
		 	try: 
		 		path.ls(path.delete_path).index(arg) #find can't be used on lists
		 		originalpath = '' 
		 		file = open(path.full_info_path(arg))
		 		for lines in file:
		 			if lines.startswith('Path'):
		 				originalpath = lines[5:-1] # get original filename
		 				# and check name doesn't already exist in file
		 				originalpath = path.join(path.path_sans_filename(originalpath),test_duplicate(path.filename(arg), originalpath))
		 		file.close()
				if options.blprompt == True:
					if raw_input("restore '%s'?" % arg) in ['y','Y','yes','YES']: pass
					else: continue		 		
		 		move(path.full_delete_path(arg),originalpath)
		 		os.remove(path.full_info_path(arg))
		 		if options.blverbose == True:
		 			print '%s restored to %s' % (arg, originalpath)
		 	except ValueError:
		 		sys.stderr.write('%s not found\n' % arg)		
		 				
	return 0

if __name__ == '__main__': main()

```

---

### Post by emigrant on 2009-11-07
thank you very much for the script [benj1]("http://ubuntuforums.org/member.php?u=679960"),
its perfectly working  :)

---

