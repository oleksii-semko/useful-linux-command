useful-linux-command
====================
------------------------------------------------
You can add any commands or improve existing one
However, you must follow the current pattern is:

# THE_LINUX_COMMAND_EXPLANATION
THE_LINUX_COMMAND_1
THE_LINUX_COMMAND_2
...
------------------------------------------------

Find relatives
==============

# find string in file
find . -name MY_FILE_PATTERN | xargs grep 'MY_STRING'
# same as above, but just with the file name
find . -name "MY_FILE_PATTERN" -exec grep -l MY_STRING {} \;
# find string in file and give, with, before each file name, the number of time the MY_STRING appears in the file
find . -name "MY_FILE_PATTERN" | xargs grep 'MY_STRING' | awk -F: '{print $1}' | uniq -c
# less on a source file with syntax highlighting (need highlight : http://www.andre-simon.de/doku/highlight/en/highlight.html)
highlight -l -A SOURCE_FILE  | less -R
# find string in specified path and file pattern
find . -ipath './MY_DIRECTORY/FOOBAR/*/*.MY_EXTENSION' | xargs grep 'MY_STRING'
# open files in editor which string match in files
gedit `find . -ipath './MY_DIRECTORY/FOOBAR/*/*.MY_EXTENSION' | xargs grep 'MY_STRING' | awk -F: '{print $1}'`
# open files in editor which string match in files
find . -ipath './MY_DIRECTORY/FOOBAR/*/*.MY_EXTENSION' -exec perl -pi -e 's/MY_ORIG_STRING/MY_REPLACED_STRING/' {} \;

# replace string in files which strings match in files
find . -ipath './merlin-data/src/*/*.xml' -exec perl -pi -e 's/http:\/\/hibernate.sourceforge.net\//http:\/\/www.hibernate.org\/dtd\//' {} \;
# Another way to replace string in files 
perl -p -i -e 's/relativePath>../relativePath>..\/../g' `find ./ -name pom.xml`

# delete files recursively
$ find . -name .DS_Store -delete

#Find all those pesky files above 20mb
find . -size +20000k -exec du -h {} \;


media relatives
===============

# erase a CDRW
sudo cdrecord blank=all -immed dev=/dev/cdrw

# mount an Iso file
mount -o loop -t iso9660 file.iso /media/iso

# extract audio from a video (without reencoding it)
ffmpeg -i mandelbrot.flv -vn -acodec copy mandelbrot.mp3

Bash relatives
=============

# Delete last word from command line
CTRL + W 

# Delate current line from command line
CTRL + U

# Logout current terminal
CTRL + D

# Recursive search
CTRL + R

# Clear screen
CTRL + L

# Change under ubuntu the default color of directory that is other-writable (o+w) and not sticky, see: http://www.bigsoft.co.uk/blog/index.php/2008/04/11/configuring-ls_colors
echo "OTHER_WRITABLE 01;34" > ~/.dircolors

System relatives
================

# display a desktop notification
notify-send "Title" "This is a message"

# When the system's freezed :
Keep Left Alt & Print Screen pressed, then R, S, E, I, U, B (Raising a Skinny Elephant Is Utterly Boring)

# Find broken symlinks in a specified directory
for i in `find MY_DIRECTORY -type l`; do [ -e $i ] || echo $i is broken; done

# Get BIOS version
sudo dmidecode -s bios-version

Simply commands
===============

# kill a process by its window
xkill #And squeeze the trigger

Display relatives
================

# Send display to specific output
xrandr --output HDMI1 --right-of LVDS1
