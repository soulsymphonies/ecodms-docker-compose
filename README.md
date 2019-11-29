# ecodms-docker-compose
Running Ecodms in a docker environment, using docker compose

This docker-compose file creates a container for ecodms 18.09 with persistent data store.
You can either take the storage layout, or choose your own folders by editing the docker-compose file.

## Data storage
Ecodms document and database data will be stored in a subfolder called ```data/ecodmsData``` relative to path where the docker-compose file is stored.
The same is true for the scaninput folder, which will be stored in a subfolder called data/scaninput

For example, if the docker-compose file is places in ```/opt/ecodms```, then the data folder will be ```/opt/ecodms/data/ecodmsData``` and the scan folder will be ```/opt/ecodms/data/scaninput```

## Backup and Restore
Ecodms has the capability to easily create backups and to be easily restored. For this there exist two folders, which in this case are placed under ```/data/ecodms-backup``` and ```/data/ecodms-restore```

If you want to backup your ecodms container data, just create an empty file called "create" in the backup folder, shortly after the backup will be created as a zip file and then the "create" file will be removed

For example: ```touch /data/ecodms-backup/create```

If you want to restore a backup then place one of the *.zip files that you have created in the folder ```/data/ecodms-restore``` and remname it to ```restore.zip```.
Then restart the container with ```docker-compose down && docker-compose up -d``` and the restore will be performed

**BUT BE AWARE,  this will overwrite *ALL DATA* in the ecodms container with the data from ```restore.zip```**
