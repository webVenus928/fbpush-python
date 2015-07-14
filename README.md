# fbpush
**fbpush** is a CLI tool to push config files to Juniper network devices. 


## Requirements
fbpush requires or works with
* Mac OS X or Linux
* Python 2.6.* or 2.7.*


## Installation

*   Clone the project from the github repository
    *   `git clone https://github.com/facebook/fbpush.git`

*   Go to the Project Directory install using setup.py
    *   `sudo python setup.py install`

*   The sample config files are stored in **/var/lib/fbpush/config** .
    *   **devices.json** contains the network device details   
    *   **configuration.json** contians the config variables
    *   **The default directory can be changed by passing --config-dir='/path/to/directory'**

* The devices.json contains a list of device details dictonary. The attributes currently supported out of box are:
    *    **"name"** : name of the device
    *    **"vendor"** : name of the device vendor
    *    **"location"** :  location of the device
    *    **"ip"** : ip of the device
    
* Adding new attributes to the above list is easy, just change the **OPTION_ATTRS** in configuration.json and add the same to devices.json.   
    
* The **configuration.json** contains a list of configuration  variables for the fbpush tool.  

  

**fbpush is now ready to use.**   

## How to use fbpush

* Prepare the config files 
  * A sample config file could look like (if you are lazy one can be found in home directory too with name **sample.conf**)-      
    ```
    /* $Id:$ name: <device_name>; vendors: juniper */
    /* Generated by <user> at Thu May  7 00:27:28 2015, apply with fbpush or "load replace terminal" */
    groups {
        <user>-TEST {
            }
    }
    ```   
  * Replace the **&lt;device_name&gt;** and the **&lt;user&gt;** in the above and the sample.conf is ready to test.    
* Dry Run is currently compulsary (unless the --clowntown flag is set).
    *   ``` $ fbpush -n sample.conf  ```
* After dry run is succesful user should review the diff files. If the diff file looks correct conduct the actual push using
    *   ``` $ fbpush sample.conf ``` 


## Full documentation

**The following options are provided by the command line parser of fbpush. -**

## Options: ##
    -h, --help                                                          Display the Help Message   
    --names=NAMES                                                       Filter the devices based on name,    
    --vendors=VENDORS                                                   Filter based on vendors,     
    --locations=LOCATIONS                                               Filter based on locations, 
    
    --name_regex=NAME_REGEX                                             Regex filter based on names,   
    --vendor_regex=VENDOR_REGEX                                         Regex filter based on vendors,
    --location_regex=LOCATION_REGEX                                     Regex filter based on locations,   
    
    --exclude_name_regex=EXCLUDE_NAME_REGEX                             Exclude regex filter based on names,   
    --exclude_vendor_regex=EXCLUDE_VENDOR_REGEX                         Exclude regex filter based on vendors, 
    --exclude_location_regex=EXCLUDE_ROLE_REGEX                         Exclude regex filter based on locations, 

    --config-dir=/path/to/config/dir                                    Use it if the config files reside in some other directory than default directory,
    -u USERNAME, --user=USERNAME                                        Username to be used to login to the network device (Optional Unix Username by default)  
    -p PASSWORD, --pass=PASSWORD                                        Password for the above User
    -c CONFIRMED_IN, --confirmed_in=CONFIRMED_IN    
    -r ROLLBACK_IN, --rollback_in=ROLLBACK_IN  
    -a, --atomic                                                        All or nothing  
    -f, --force                                                         Force the config files into network device without dry run.
    --gen_md5                                                           Generate the md5 hash for the config run
    -n, --dry_run                                                       Giver dry run to the config file without really changing anything
    -m, --multiple_diffs  
    -x, --xml  
    -d DIFF_DIR, --diff_dir=DIFF_DIR  
    --stdin  
    --color  
    --clowntown  
    --xml_debug  
    --full_comments                                                     Dont't filter out the comments from the config files
    --no_commit_full  

**NOTE : All the regex based filters are pythonic regex.**

## Running Tests
* The tests can be run via setup.py using:
* * ```sudo python setup.py test```



## Join the fbpush community
* Website:  
* Facebook page:  
* Mailing list  
* irc:    
* **Pull request are always welcome. See the CONTRIBUTING file for how to help out.***  

## License
fbpush is BSD-licensed. We also provide an additional patent grant.
