# scripts

Utility scripts for self-hosted services.

## Scripts

### `launch`

Manages Docker Compose stacks. It auto-discovers any subdirectory one level deep that contains a compose file (`docker-compose.yml`, `docker-compose.yaml`, `compose.yml`, or `compose.yaml`).

**Usage**

```
launch <command> [subdir]
```

**Commands**

| Command | Description |
|---|---|
| `start [subdir]` | Start all stacks, or a specific one |
| `stop [subdir]` | Stop all stacks, or a specific one |
| `restart [subdir]` | Restart all stacks, or a specific one |
| `pull [subdir]` | Pull latest images for all stacks, or a specific one |
| `status` | Show container status for all stacks |

**Examples**

```bash
# Start everything
launch start

# Start a single stack
launch start my-app

# Pull new images and restart one stack
launch pull my-app
launch restart my-app

# See what's running
launch status
```

**Stack discovery**

The script looks for poo compose files in `<script-dir>/*/<compose-file>`. Each matching subdirectory is treated as a stack, named after the directory. The script must live alongside (or above) the stack directories — it uses its own location as the base path.
