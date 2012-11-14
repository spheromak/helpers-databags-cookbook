# helpers-databags cookbook
This recipe brings in a `Helpers::DataBags` module that povides extra methods for dealing with databags

# Usage
Include this recipe in your run_list and mix it into whatever namespace you need it in.

* mix_recipe.rb  recipe exists to auto mix to recipes and as an example

you can Open up and mix these methods in other namespaces if needed
     
      class Chef
        class Template
          include Helpers::DataBags  
        end
      end

# Methods
### escape_bagname
|args|type|default|
|name|string| |

This method takes a string and escapes invalid data-bag characters int the following ways:
* dot to dash: `.` -> `-`
* space to underscore:` ` -> `_`
  

### data_bag_fqdn 
|args|type|default|
|fqdn|string|`node[:fqdn]`|

This is just a wrapper around escape bagname used when calling databag items that match node[:fqdn]

      data_bag_item( :mybag, data_bag_fqdn ) 


# Recipes
## default
  Does nothing, just makes sure the libs are loaded

## mix_recipe
Mixes the methods into Chef::Recipe 


# Author
Author:: Jesse Nelson (<spheromak@gmail.com>)
