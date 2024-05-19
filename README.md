# To use the overlay 

If you are using flakes to configure your system, add to your nixpkgs overlays attribute (examples will differ, the following is for home-manager):

```nix
{
  inputs.neovim-nightly-overlay.url = "github:nix-community/neovim-nightly-overlay";
  outputs = { self, ... }@inputs:
    let
      overlays = [
          inputs.neovim-nightly-overlay.overlay
        ];
    in
      homeConfigurations = {
        macbook-pro = inputs.home-manager.lib.homeManagerConfiguration {
          configuration = { pkgs, ... }:
            {
              nixpkgs.overlays = overlays;
            };
        };
      };
}
```
