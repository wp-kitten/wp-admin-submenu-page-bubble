wp-admin-submenu-page-bubble
============================

Custom function to use when creating submenu pages where you need to display a count bubble


## Usage

```php
add_action( 'admin_menu', 'wpk_AddSubmenuPageBubble' );
function wpk_AddSubmenuPageBubble()
{
    //-- Get here the number you want to display in the bubble
    //-- For the sake of this example I've used rand()
    //-- you can use global $wpdb if you need to extract data from db
    $number = rand(1,10);
    $title = sprintf(__('%d updates available','text-domain'), $number);
    $menuText = sprintf(__('Updates %s'),
        "<span class='update-plugins count-$number' title='$title'>
            <span class='update-count'>".number_format_i18n($number)."</span></span>");
    add_submenu_page('parent-slug', 'Updates', $menuText, 'read', 'updates', 'UpdatesPage');
}
```

This will create the submenu page under your plugin's main menu and add the number of updates
in the bubble, just like WordPress shows the number of comments or updates.