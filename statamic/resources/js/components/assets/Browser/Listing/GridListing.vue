<template>

    <div class="asset-grid-listing">

        <div class="asset-tile is-folder"
             @click.prevent="selectFolder(folder.parent_path)"
             v-if="hasParent && !restrictNavigation">
            <div class="asset-thumb-container">
                <file-icon type="div" extension="folder"></file-icon>
            </div>
            <div class="asset-meta">
                <div class="asset-filename">..</div>
            </div>
        </div>

        <folder-tile
            v-for="folder in subfolders"
            :folder="folder"
            @selected="selectFolder"
            @editing="editFolder"
            @deleting="deleteFolder">
        </folder-tile>

        <asset-tile
            v-for="asset in assets"
            :asset="asset"
            :selected-assets="selectedAssets"
            @selected="selectAsset"
            @deselected="deselectAsset"
            @editing="editAsset"
            @doubleclicked="assetDoubleclicked">
        </asset-tile>

    </div>

</template>


<script>
import Listing from './Listing';

export default {

    mixins: [Listing],


    components: {
        AssetTile: require('./AssetTile.vue'),
        FolderTile: require('./FolderTile.vue')
    },

}
</script>
